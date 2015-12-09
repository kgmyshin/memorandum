### モバイルアプリの成功を支える最新技術トレンド

松内良介

##### 進化し続けるAndroid プラットフォーム

14億台M(去年は10億台)

10月 Anroid 6.0

  - Perimssion
  - Now onTap
  - App link
  - Android pay
  - Battery
  - Finger print

New Devices

- Pixcel C
- Nexsus 5s
- Nexsus 6p
- chromecast

Multi screens

- androidtv
- chromecast
- Google cardboard
- androidwear
- android auto

Tool

- Android Studio 2.0 (preview) from canary channel
  - buildが早くなった
  - 次の世代のエミュレーター
  - GPU profiler

##### Google playによるアプリ経済圏の広がり

US$ 7,000,000,000

決済方法の広がり
- キャリア決済 37 Countries
- ギフトカード 30 countries
- Paypal 24 countries

力を入れていく

- Google play for family
- Android for work

Go Global

##### いま注目すべき技術トレンド

- Develop your app
- Engage with users
- Earn more money

高品質UI + シームレスな繊維・サインイン

- Materiad design (not 標準虫の独自UI)
- Smart Lock for passwords Google sign in (not いちちパスワード入力)
- オフライン体験(sync adapter)

ユーザとアプリの出会いの進化

1. Google playストアの強化
  - 検索。Discovery強化
  - Serach Ads on Google play
2. App Indexing
  - Google検索 -> アプリ内の動線
  - 「ホーム画面からの起動」以外の動線
3. 広告技術イノベーション
  - AdMob, AdWordsの進化
  - Analyticsの進化
  - Native Adsの普及

ユーザの文脈(TPO)に応じたコンテンツ提供

- Google  Maps API Fused Location Provider Activity Recognition
- Beacons (Eddystone)
- (Web) Push notifications
- (App) 通知表現のリッチ化

近接通信とマルチスクリーン

- Nearby Messages API
- Nearby Connections API
- Bluetooth Low Energy
- NFC
- Wifi

進化を続けるクラウド基盤 + 機械学習技術

- 柔軟なスケーラビリティ実現
- コンテナ技術
- リアルタイム(非バッチ)化
- Cloud Vision API(Preview0

- BigQueryなどによる分析生産性の向上
- 機械学習技術の普及(Tensor Flow)

動画の利用シーンの拡大

1. 動画広告の普及
2. ゲーム実況動画の魅力向上
3. Youtube 36--degree video
4. ExoPlayerライブラリ
5. 4k映像表現


### マテリアルデザインでよりよいユーザー体験を実現しよう
星竜一さん

マテリアルデザインをなぜ開発したか

##### 昔は

同じGmailでも

Gmail.com, Android, Mobile Web

見た目がバラバラだった。

-> ユーザはそれぞれのプラットフォームについて学ばないと使えない

  ex. ラベル機能はAndroidではどこにあるの？

##### 2011

Project Kennedyを立ち上げた

バラバラだったGoogleのプロダクトに一貫したデザインを持たせよう
ユーザにも高い体験をしてもらえるように

Googleの上の黒いステータスバーのやつ

ただAndroidはAndroidで独自のデザインだった (Holo)

KennedyとHoloで違う

ユーザ体験バラバラでいいの？

これは業界全体での問題だった。

##### 2014

project kennedyのチーム、Androidのチームなどのデザイナーで考えた

モバイルでの使い方を知っていればタブレットでもデスクトップでも使える。

これを意識した。

##### どのようなコンセプトで作られているか？

1. タンジブルサーフェス
  1つの紙(電子ペーパー)でできていると考える (マテリアルデザインのベースとなる考え方)

  紙なので重ねたら影がついたりする、、などを自然に想像出来る
  
  -> **高さ** という概念が入ってくる
  
  高さを使うことでユーザがどこに注意を向けるべきかを一貫した方法で知らせることができる
  
  Dialog, Floating Action Bar
  
  「手前にあるものほど、ユーザは注意を向けてください」という意図がある
  
  インタラクションの手がかり (スクロールと固定0

2. 印刷物のようなデザイン
  
  print-like design
  
  ベースライン グリッド * キーライン
  
  フォントの変更 (Roboto)

3. 意味があるアニメーション

  装飾ではない。何かしらの意味のあるもの
  
  instructive motion
  
  人は動くものに惹きつけられる
  
  -> 再生したらコントローロパネルを見て欲しい
    -> コントロールパネルをアニメーションすることで注目される

4. アダプティブデザイン

Master / detail

sたておfマテリアl(マテリアルデザインをさいようしたじゃああr

g.co/materialshowcase				
  

### 高品質Androidアプリ実装ヒント集 - ゴミアプリと言わせないために

ガイドライン資料
Google play ベスト21015

- アプリ品質

google Playでのユーザ評価と収益性

3-3.9と4以上では収益が4倍

資料

- The secrets to app success on google play
- Mobile App Ux Principles
- google Designサイトの各種記事
  - Design from iOS to Android (and back again)



App Quiality ガイドライン
- 重要  

ベストオブ2015
評価軸は

-  高いユーザ評価、高品質
-  Android標準にしたがった使いやすいUIデザイン


ユーザ評価

- アプリである意味がない
  - Webサイトよりも早く目的の情報にたどりつける
  - 動作や表示が軽快で捜査官が気持ちよい
  - オフラインでも使える (データ通信が少ない0
- 遅い、思い
　- アプリ動作をあげる
　- 
- 電池を使いすぎる
  - 使わないときもずっと裏で動いてるとか
  - battery statsとかBattery Histroian
  - JobSchedulure API
  - Dozeモード、App Stanby
  - 端末が寝たいときは寝かせてあげてください
- ネットワークを使いすぎる、オフラインで使えない
- いつも居座っている
  - memory monitor toold
- Backボタン対応がデタラメ
- 新しい機種/OSバージョンに非対応
- ユーザ数の増加にサーバー設備が追いついてない
  - 最近オープンベータ機能がつかえる
- 位置情報の取得処理がデタラメ
  - Fused Location Providerの低精度モード(Coarse Location)とかもいいかも
  - onStopでとめる
- パーミッション要求が不審
  - 実行時パーミッション対応しよう
- タブレットユーザ無視
  - タブレット対応しよう
  - タブレットユーザの方が課金率いいよ!(1.7x)
- サインイン、会員登録が面倒
  - Smart Lock for passwords
  - Google sign in
- 通知、故国やポップアップがうるさい
- UIがもだんではない
  - 全部Webviewでしょ？
  - Material Designつかおう
- マルチスクリーン時代のおもてなし



### スマートフォン体験を一歩先へ- プログレッシブウェブアプリの作り方

Physical Web

1:49 スマートフォンの月間利用時間

- 1:28 App
- 0:23 Web

スマートフォンユーザの時間 80% はその人のトップ3アプリに費やされている

スマートフォンユーザの平均月間利用アプリ数 25
chrome for androidユーザの平均月間訪問サイト数 100+

Progressive Web Apps

- インデックスに登録できる
- 検索できる
- Native appのような体験
- 最新のブラウザであれば最新の挙動、古ければそれに従った挙動

##### 「Flipkart」

React.js

ホーム画面に追加
-> 開く
-> フルスクリーン (ブラウザじゃない？？？？)
-> オフラインもなるべく対応(prefetchしてる)
-> RecentViewを見ても、Native Like

- アプリインストールバナー(ホーム画面に追加しませんか？とクロームが効いてくれる)
	- manifest定義
	- Service Worker
	- Httpsで提供
	- 5分以上の間隔で複数回アクセス

- manifest定義
  - manifest.jsonを作る
  - `<link ref="manifest" href="/manifest.json" />`
	  
- Service Worker
  - Cache API
  - Push Notification
  - https://github.com/GoogleChrome/application-shell
  - Background sync
  - Periodic Sync


### ユーザーとコンテンツの距離を縮めよう - コンテキストウェアなアプリケーション

##### コンテンツまでの距離

- 何かを知りたい
- どこかへ行きたい
- 何かを買いたい

お気に入りのアプリのみが使われる

モバイルの時間の72%を27のアプリが占める
- 月に一回以上 27個
- 月に10回以上9個

秘書的なアプリになろう！！！

どういう秘書がいい？

- その人がやって欲しいことを前もってやってくれる

ユーザがコンテンツまでのステップと離脱率

ステップを一つ重ねるごとに **20%** のユーザが離脱

各ステップの所要時間と離脱率

- 各ステップにかかる時間が延びても離脱率は増加
- 1s越えるとコンテキストスイッチが発生
- それ以上は別のことを考え出す

近くのレストランをアプリで検索して予約sルウ

##### コンテキスト

ユーザーの入力以外の情報をどれだけ多く読み取れるか

端末の種類、時間、履歴、etc...測りきれないほどの情報

##### ステップの省略・短縮

Googleはそのために何を提供しているのか

- Smart Lock for psswords
  - 既存の認証システムを変えずにユーザのログイン作業を軽減。無くしたいときに
- App Indexing
  - 検索結果の中にネイティブアプリケーションリンク
  - Google検索の履歴にアプリへのリンクを表示
- Now on Tap
  - ユーザに検索バーへの入力させなくてもよい (コンテキストを読み取る)
- Eddystone 
  - Physical Webに対応したBLEビーコン規格
- Service Worker
  - ブラウザ内でバックグラウンドで非同期な処理を可能にする
- Accelerated Mobile Pages(AMP)
  - モバイルページの表示時間を早めよう
    - HTMLで表示を高速化
      - 気泡を限定的にしコンテンツリソースを制限
      - カスタムタグでリソース自体はリッチに表現
      - おり地鳴りコンテンツへのフォールバックも可能
      - オープンソースで使用を策定
      - 2016年前半にサービス公開開始  

##### コンテンツを分解する

コンテキストに沿った内容と補助的なアクション

リッチな通知を使いこなす

通知とAndroid Wear

  - 通知を見るためだけにポケットからモバイル端末を出す必要があるのか

### ユーザーの心をつかむデザイン

Designe of awa

awaのfeatures

- プレイリストを軸に音楽との「出会い」と「再開」を演出
- 聴いた曲やお気に入りにした曲などを分析してあなた好みの楽曲をリコメンド
- 最新のトレンド曲やジャンルl気分でプレイリストを選ぶことができる
- 好きな曲やアーティストと雰囲気が近い曲をノンストップで流す
- こだわり選挙区でプレイリストを作成してSNSシェア
- おフライ再生やスマートフォンにあるローカル音源の再生も可能

##### 没頭して聞くためのデザイン -awaができるまで-

オリエン -> 提出&Feedback -> ベースが完成

「キーワード」
- クール
- 海外アプリのようなインパクト
- 感覚

1. CD Storeにいく
  - 実際の音楽を提供する場はどうなってるんだっけ？を体験

2. 本屋にいく
  - 雑誌のデザインがいい
    - ターゲットが明確
    - デザインの引き出しが多い
    - とんまながしっかりしている

3. いろんなアプリを触る

突然のひらめきなんてない「繊細かつ大胆なレイアウト」をひたすら考える

伝えるために作る

考えたラフデザインをチームに伝えるため実際にデザインして提案した

##### 「没頭」を「継続」につなげるためにデザインに何ができるのか

"没頭"を"継続"とは「毎日つかいたくなる」

- UIの目的
  - つかいやすさ * 「印象」「洗練されたインタラクション」
- UXの目的
  - アプリを立ち上げたらすぐ再生
  
- Sense & Logic 感覚と理論
  - 目的を明確にして、感覚で出会いんしたのちに。理論に基づき設計

- Scrap & Build 
  - 作ったものは常に破壊が前提。さらにいいものをチーム全員で再生していくイメージ

Philosophy

  1. 受け身にならない・使用はまたない
  2. 
  3. どんどん作る

コミュニケーションのときにたいせつにしていること
  - 言いたいことはちゃんと話し合う
  - 浅くいいから広くエンジニアの知識を得る
  - 年次に関係なく相手の仕事を尊重する
 
デザイナーは「設計士」

##### ユーザの反応をどうデザインに反映させるか

全員で企画して、全員で決める

「ユーザのために」ではなく「自分がどうつかいたいのか」
自分たちが「ユーザ」であるべき

### Android TV, ChromecastとNearby APIの近接通信で実現するマルチスクリーン体験

#####  cast対応のアプリ開発
  - スマホ・タブレットのアプリまたはchromeブラウザ上でcastアイコンをタップ
  - cast対応デバイス上でreceiverアプリが起動、receiverアプリはインターネットからコンテンツをストリーム開始
  - 再生中はSenderアプリとReceiverアプリの間で必要に応じた通信が可能

スマホ・タブレットがリモコン

#####  cast対応アプリの公開フロー
  - 実現したい体験に応じてReceiverの種類を選択
		- Default Receiver
		- stylede media player
		- custom receiver
  - Senderアプリを開発
  - Google Cast SDK Developer ConsoleでReceiverアプリ情報を登録
  - Google PlayまたはAppStoreで対応Senderアプリを公開

#####  新しいGoogle cast api
  - remote display api
	    -  Senderアプリが画面描画 -> Castに送信
	      - Unityプラグイン公開
  - game manager api
	    -  Reciverアプリがゲーム状態管理
	    -  ReceiverアプリはHTML, CSS, Javascriptでゲーム画面更新
	    -  新ゲーム公開中 Just Dance Now, Monopoly Here % Now...
  - よりインtならクティブなマルチスクリーン体験が実現可能に

- Android TV

##### 概要
  - Android 5.0+
  - モバイルとほぼ同様
  - ただタッチがつかえない
  - 非搭載Googleアプリ、 Chorme, Gmail
  - 標準プラットフォーム機能
    -  ホーム画面、オン背によるコンテンツ件sなく機能など
  - 各製品目かー様による機能追加
    - テレビ放送受信
    - ホーム画面カスタマイズ

##### Android TVアプリの開発・公開のながれ

1. Android TV対応アプリを開発
  - 既存アプリへの機能追加
  - TV専用アプリとしての公開
2. Google Play developer consoleにアップロード「Android TVに配信」をチェック
3. googleの新sナゴにAndroid TV上のGoogle Playストアで公開
　- モバイル版同様β機能とかも使える

##### 動画再生プレイヤー

- ExoPlayerライブラリ
  - Githubにあるよ
  - 4k映像再生可
- 標準MediaPlayer API
- Youtube IFrame Player API(WebView)
- なんらかの自社製、他社製プレイヤー製品

#####  ライブラリ + 参照ソースコードガイドライン

- Leanbackライブラリ
  - ガイドライン推奨のUIパターンの骨組み
    - BrowseView, DetailViewの標準的な実装
-  githubのsampleコード
    -  android-UniversalMusicPlayer
    -  androidtv-Leanback
-  Android TV Design Guidlines
    -  UIデザインの指針


##### 近接通信とNearby API

- Nearby API
   - 物理的に近い距離の端末を自動的に探して通信
   - AndroidとiOSの両対応
   - Nearby Message API
     - 近くの端末をBL, BLE, Wifi, 超音波で発見
     - 端末は同じLANじゃなくてよい
     - Pub/sub型のやりとり
- 従来の通信手段     
  - BL
  - NFC
  - Wifi

##### 活用例

- Trello
- Pocket Casts
- Trulia

##### 近接通信の構成例

- mobile 2 mobile
- mobile 2 tv
- mobile 2 cast

##### 近接通信技術により広がるマルチスクリーン体験の可能性

- andoridtv
- chromecast
- cardboard
- wear
- auto



