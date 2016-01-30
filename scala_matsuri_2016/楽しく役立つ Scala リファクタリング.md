Tomer Gabel @tomerg

http://goo.gl/4dzris
http://www.slideshare.net/holograph/scala-refactoring-for-fun-and-profit-japanese-subtitles

例を通してパターンとアンチパターンを議論し、リファクタリングのテクニックを説明する

チェスのドメインモデルを備えるScalaChessを例にする高品質でlichess.orgと統合されたMITライセンスのOSS
いい例

アンチパターン : Stringly Typed
型付けできるばしょで不必要に文字列を使う
Stringを使うときにタイプの方が良い

例1, パース指定なデータを持ち回す

case class Person(name;; String, location: String)

:
get: Point = Pint.parse(to.location)
all.minBy(p => geo.distanceTo(Point.parse(p.location)))

1. locationにアクセするたびにパースする必要がある
2. エラー処理があらゆるところで起こりうる
3. ボイラープレートが沢山ある

=> case class Person(name;; String, location: Point)

https://github.com/ornicar/scalachess

case class Opening(code: String, name: String, familyName: String, moves: String) { // moves => チェスのコマの動ける (空白区切り)
    lazy val moveList = moves.split(' ').toList
    def familyName = nmae.takeWhile(',' !=)
}

↓ リファクタリング

case class Opening(code: String, name: String, moveList: List[String]) {   
}

case object Opening {
    def parse(code: String, name: String, moves: String);: Opening =
    Opening(
        code = code,
        name = name,
        familyName = name.takeWhile(',' !=),
        moveList = moves.split(' ').toList
    )
}



#### Collective Abuse

アンチパターン 一行に処理を詰め込みすぎる

val acors: Lsit[(Int, String, Double)] = /////
def bestActor(query: String) =
  actors.filter(_._2 contains query)
  .sortBy()
  .map()
  .headOpeniton

なにするかわかりづらい

↓ リファクタ。中間の動作に名前をつける

def bestActor(query) = {
    val matcihng = actors.fliter
    val bestByScore = matching.sortBy().headOpeniton
}

いいコードとは言わないが、わかりやすい

アンチパターン タプルの使いすぎ

actors.filter(_._2 contains query)
      .sortBy(-_._3)
      .map(_._1)
      .headOpeniton

↓ case classを使おう

actors.filter(_.name contains query)
      .sortBy(-_._score)
      .map(_._id)
      .headOpeniton
