scalaでドメイン駆動設計に真正面から取り組んだ話

@yoshiyoshifujii

DDDは本見てもむずい、迷う

今日の話 -> 悩みながらどうやっていったか、その中で得た知見

・レイヤーアーキテクチャー
・CQRS
・is-a root entity
・Messages

### レイヤーアーキテクチャー

ポイント
- レイヤーの責務を明確
- かいレイヤのみに依存
- ドメインを明確

UIレイヤー => UI
アプリケーションレイヤー => ソフトウェアの仕事を定義
ドメインレイヤー => ビジネスロジック
Infraレイヤー => 上位を支える技術的機能を提供

UI      App           Domain    Infra
Form => View Model => Entity => SQL
Json <= View Model <= Entity <= Result

ビジネスロジックが各レイヤーに混ざってしまった。。

どう解決するか？ =>
- Communication
- レビューで解決
- 分析モデリングというイベントを用意した
  何をドメインロジックなのかをUMLを使ってmtg


Service of three types
- Application Service
- Domain Service
- Infra Service


どうやってサービスを扱うか? =>
- 一度アプリケーションサービスに寄せる
- ただしこれは一時的な処置
- 後にリファクタリングする


コンバート処理が多い...
  Form => View Model => Entity => SQL
  Json <= View Model <= Entity <= Result
7回コンバートしとる => 仕方ない...

ドメインを隔離するのがDDDだ
コンバートすることでレイヤー間の責務が明確になるよね

とはいえ、多い。

Command Query Responsibity Segregation

### Command Query Responsibity Segregation

CQRS

あらゆるメソッドはコマンドもしくはクエリ。その療法はNG
  Command query separation

ドメイン駆動設計はソフトウェアの複雑性をなくすことなのに、逆に複雑にしてない？

単純に一覧表示するだけとかなら Query Modelでいい

Form => View Model => SQL
Json <= Query MOdel <= Record

QueryModelはインフラ層にいる

Command Modelはレイヤー化アーキテクチャのままでやるので使わなかった。

単純な取得処理はクエリとして分離、それ以外はレイヤー化アーキテクチャ


### is-a Root Entity

Root Entity
 has, is

Root Entity
↑        ↑
Sub1     Sub2

is-a はややこしい
One Repository? Two Repositories? (Sub1Repository, Sub2Repository)
ジェネリクスで対応

### Message

浅いレイヤーのメッセージは返しやすい。
深いレイヤーの場合のエラーメッセージは。。
 => 復旧不可能なエラーが多い
 => ログに履いて終わるようにする
ドメインレイヤーの場合はエラーメッッセージは...

どうやって実装するか？
- Option
- Either Single message only
- Try    throw形式でかきやすい
- Validation(Scalaz) エラーをどんどんスタックさせて返すことができる

Stack or not?
 Yes => Validation
 No => Try or Either

ValidationはMonadじゃないのでちょっと辛いところある。
