Yuichi Araki
普段はサポートライブラリーの開発をやってる

preview4まではapiが変わる可能性がある
preview4でapi levelが24になる予定

新機能

- マルチウィンドウ
- 通知の強化
- java8

動作変更

- バックグラウンド処理の最適化
- 言語設定

## マルチウィンドウ

- 二分式
 電話、タブレットではほとんどの場合2分割 (真ん中の線をドラッグできる)

- 自由形式

 ？？ まだ入ってない。

- picture in picture (Android TV限定の機能)


下記にどう対応するか
- 画面に表示されてるけど、アクティブじゃない
  =>
- リサイズされる
  => 今まで通り

ライフサイクルはこれまで通り

画面リサイズ時 => 画面回転と同じ(onPauseではなくonStop)

アクティブ(onResumeが呼ばれた方)/非アクティブ

唯一気をつけたい
=> 動画を再生する。動画を見ながらTwitterしたい。
   動画アプリにはonPauseが来る。
   onPauseで動画を止めてはいけない。onStopで止める。


AndroidManifest.xml

リサイズできるかどうか
android:resizableActivity=true/false(default true)
(targetSdkがNでないものはtrue扱いされる)


マルチウィンドウサイズ
<layout minimalHeight="" minimalWidth="" defaultHeight="" defaultWidth="" />
が指定できる。

マルチウィンドウ判定(Activityとfragment)
- isInMutliWindowMode()
- onMultiWidnowModeChannged()


マルチウィンドウの切り替え方法

分割・自由形式
アプリ側から制御できない。ユーザーが操作する。


ドラッグアンドドロップ

View.startDragAndDrop() DRAG_FLAG_GLOBAL 分割のもう一方の方向にドラッグできる
View.cancelDragAndDrop() ドラッグ中のものをキャンセル
View.updateDragShadow() ドラッグ中の表示をキャンセル


## 通知

通知のなかから直接返信できる
Android Wearようにもともとあったが、電話・タブレットで動くようになった

API追加
Notification.Builder.setReomoteInputHisotry() 履歴
Notification.Builder.setGroup() グループ化

Notificationへのカスタムビューの設定方法が変わった

setCustomContentView/setStyleが追加、setContentViewはdep

## java8

```
  jackOptions {
      enable true
  }
```

通常のjava8は動かない。

ラムダは後方互換あり、インターフェースのデフォルトメソッド、性的メソッド、反復アノテーション、新しいAPIはAndroidN以降のみ使用可能

ラムダは内部では結局リスナーをnewしているような感じで動く

## データセーバー

データを節約できるようになる
ユーザーがホワイトリストに入れたもの以外はバックグラウンドで通信できなくなる

自分がホワイトリストかどうかの判定ができる

getRestrictBackgroundStatus()
RESTRICT_BACKGROUND_ENABLED => バックグラウンドで通信できない
RESTRICT_BACKGROUND_WHITELISTED => バックグラウンドでも通信できる
RESTRICT_BACKGROUND_DISABLED => 通常通り

## クイック設定

ドラッグアンドドロップで項目を追加・削除できる

andorid.service.quicksettings

- Tile
- TileService

## Scoped Directory Access

特定のディレクトリへの権限を要求

「いまから写真を見に行きますよ？」という許可を見に行く

## その他の新機能

- Direct Boot
- ShortcutManager(動的なショートカット)
- ICU4j (international components for unicode)
- NFC type-f host card emulation
- androi for workの拡張改善
- vulkan
- open gl ES3.2

## Doze 動作変更

Doze => 端末を休眠状態にしてバッテリー消費を抑える

ネットワーク、アラーム、GPSいろいろOFFニスル

それのうたた寝状態みたいなちょっとゆるいモードができた(ネットワークだけ)
今までのDOZEは机の上に置いておかないとならなかったけど、このゆるいモードはポケットに入れておいてもなる

何かバックグラウンドでやりたいことがあるときはジョブスケジューラーを使いましょう

## Project Svelte 動作変更

端末の電力所費を削減しようというProject

これまで来ていたintentがこなくなる

CONNECTIVIEY_ACTION => AndroidManifest.xmlに書いても呼ばれない(動的にレシーバーを建てたときは来る)
=> 代わりに jobschedulerを使おう => kitkat以前はGcmNetworkManagerを使おう

下記は廃止
- ACTION_NEW_PICTURE
- ACTION_NEW_VIDEO
=> JobInfo.Builder.addTriggerContentUri(JobInfo.TriggerContentUri)を使おう

## 表示サイズ 動作変更

設定で表示サイズを変更できるようになった

最大に拡大してもsw320dp(Nexus4くらい)まで

ベストプラクティスに従っていれば特にすることはない

sw320dpで動くか確認

## 言語設定 動作変更

順位付けして複数選択できるようになった
対応は基本的にいらないが、LocaleList.getDefault()でリストを取得できる
