Ganma!をDDDでやってみたのでどういう風にしたか

サーバー側をDDDでやってみた

なんでDDD => 前職ではやってた(by かとじゅん)
            詳しくは Septeni x Scala#1

## マンガのモデリング

初めのGanma!のマンガ配信業務について => 衆参でマンガ雑誌が公開される
この雑誌を「マガジン」と読むと決めた

マガジンにはストーリー(なると1話とか)が複数含まれる

ストーリーにはシリーズ(なるととか)がある

マガジンに関わる業務
・閲覧系 情報、新刊一覧、読める
・管理業務 作家さんとか

ストーリーほりさげ
- id
- seriesId
- authorId
- pageList ページ  S3のURL
         サブタイトル (option)

ストーリーリポジトリ 一覧、作者別一覧、シリーズ別一覧業務
                  StoryTableとの仲介が業務


ドメインそうには言葉以外のことはかかないようにしている。

ページはストーリーに集約

シリーズほりさげ
- id
- title 作品名
- authorId

シリーズリポジトリ 一覧、作者別一覧、保存業務
                SeriresTableとの仲介が業務

マガジンほりさげ
- id
- title
- itemList[MagazineItem] Story and series
- seriesbind(Option)

MagazineRepository 一覧、保存業務、ランキング => ランキングサービスにすればよかった
                   magazineTableとの仲介が業務

IDにはauto incrementがおおいが、insertするまでidを触れない => UUIDを利用した

DB -> Entity
 Infra層 / Entityは Domain層

DB取得結果からEntityを作るとき、Entityを作って返すとかくのはまずい気がした
 => インフラそうからタプルで返して、DomainでEntityのインスタンスを作っていた
 => 面倒だったのでやめた
 => ドメインそうに生データとEntityの変換のメソッドかクラスを設ける (Repositoryがもつ)
 => 実践DDDでは定義だけDomain層において実装はinfraでOK

App層でやっていること
- マガジンの取得
- マガジンの一覧やランキング
- 作家の管理
- ストーリーの管理

Repositoryとテーブル操作を全てobjectにしてしまった
- テストがこんなん
- DIできるようにしている
- RepositoryはFutureを使うようにしたが方良さそう

DDD良い
- 用語が合わされるので良い
- ドメインそうの実装が、口頭説明になるのでよい
- ドメインそうに余計なことかかなくなるのでよくなった

http://labs.septeni.co.jp/entry/20150617/1434470797
http://www.slideshare.net/yasuyukisugitani/septeni-scala3?ref=http://labs.septeni.co.jp/entry/20150617/1434470797
