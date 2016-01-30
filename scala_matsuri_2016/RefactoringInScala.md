### Refactoring in scala 

@gakuzzzz
tech to value co., Ltd.

#### Value objectをScalaでどう表現するか、どう扱うか

たとえば

```
userMap: map[Long, User] = users.map(u => u .id)
```

Map[Long, User]は意味が不明確。これは何？

##### First approach -> type alias

```
type UserId = Long
:
userMap: map[Userid, User] = users.map(u => u .id)
```

わかりやすいし、 UserIdがStringになっても楽。

ただ、依然として

```
userMap(board.id)
```

など間違えたidを渡しても問題なくなってしまう。

=> tagged type。
型にラベルをつける仕組みで。Scalazやsaplessなどで提供されている。

```
val userMap: Map[Id @@ User, User] = ...
:
boards.map { board =>
  board -> userMap(board.id) // compile error
}
```

`ID @@ User` と `ID @@ Board` は別の型になっている。
bytecodeに落ちる時はただのキャストになっている。

デメリットとしてAnyValのSubtypeと共存する場合、boxinv/unboxingが発生する。

##### Second approach -> Value Class

```
class UserId(val value: Long) extends AnyVal
case class BoardId(value: Long) extends AnyVal
```

```
val userMap: Map[Userid, User] = ...
:
boards.map { board =>
  board -> userMap(board.id) // compile error
}
```

以下の場合にメモリ割り当てが行われる
1. 値クラスが別の型として扱われる時
2. 値クラスが配列に代入される時
3. パターンマッチングなどにおいて、実行時の型検査を行う時

##### Tagged Type or Value Classes ?

メリデメ比較して、使いやすいやつで。

Tagged typeは....

Value classes はメソッドの追加が楽。

とはいえ,, どちらにしても ValueClassを一つ一つ定義するのが面倒

##### Next Approach -> Phantom types

````
case class Id[A](Value: Long) extends AnyVal
:
userMap: Map[Id[User], User] = ...
:
boards.map { board =>
  board -> userMap(board.id) // compile error
}
```

##### Summary

1. まず実際の物理表現と意味表現を分離し(Type alias)
2. 清適型検査の力をつかって間違いを検出(Tagged Type or Value Classes)
3. ジェネリクスでボイラープレートを減らす(Phatom type)

##### だが新たな問題発生。

外部ライブラリの型やレイヤーをまたぐ際に型変換をする必要が出てきた。それを毎回全て手で書いてやるのは大変すぎる。

Scalaの主要なライブラリは型変換の仕組みが大抵提供されている。

Play  -> PathBindable...
Slick -> ColmnType

##### Iso and prism

Isomorhism

trait Iso[A, B] {
  def to(a; A): B
  def from(b: B): A
}

Forall a: A, from(to(a)) == a
Forall b: A, to(from(b)) == b

Prism

trait Prsim(A, B) {
  def toOpt(a: A): Option[B]
  def from(b: B): A
}

=> Iso can be a subtype of Prism
Iso and prism は Monocle やshaplessで提供されている。
Iso だけなら Scalazにある

レイヤー変換にはisoかprismを一つ作っておけば大丈夫。

implict macroを使用することでIsoの定義を簡略化する方法もある。
まさしくImplict macroのドキュメントの具体例がISsoのものだったりする。

##### Summary2

1. レイヤー境界ではフレームワークやライブラリに応じた変換処理が必要
2. IsoやPrismを使うことで解決できてそしてDryにできる
3. さらにImplict macroを使えば楽
