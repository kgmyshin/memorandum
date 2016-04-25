Q. swift導入の噂について

まずない。javaをこよなく愛する人たちがコアなので。社内のチャットに貼られてLOL。
AOSPを監視しておくと何か前兆があるのかも。

Q. kotlinはどう？

いいんじゃないか。(あんまり興味無さそう)

Q. org.apache.http.legacyを使わないと使えないvolleyの今後は？

最近あんまりメンテされてない。今後どうなるかはちょっとわからない。僕なら他のを使う araki

Q. jack & jillを開発している意図はなんでしょう。コンパイル速度が早くなるだけでは、classファイルに影響を与えるjavaツールチェインが使えなくなるなど、欠点も多いように思えますが？

jack側でそれに変わる何かを作っているらしい。
コンパイル速度が早くなるは結構ばかにならない。
意図はない。やりたいからやってる。
Androidチーム内で年々ビルドが遅くなるというのが問題になっている。

Q. Bottom Navigation追加されたけど、どういうこと？

Material DesignのガイドラインはいろいろFeedbackをもらって、いいものであれば変わっていく。
デザイナーのマイクデビーがいっていたいたのは、タブの変わりではなくサイドから出てくるドロワーの変わりだと言っていた。

Q. マルチウィンドウは時のキーボード表示はどうなる？

横2分割のときは、アクティブな方の下からでてくる。
たて2分割はときは、下がキーボードになる。
だった気がする

Q. Android Playgroundみたいなものが欲しいです。

なさそう。

Q. Bazelにすると何がよくなるのか？Gradleはdepracatedになるのか？

Bazelは採用されないのでは？

Q. 「onPauseで音を止める、Nに限らないですが」という説明ありましたが、マルチウィンドウではonPauseで処理をとめない、という話がありました。結局どうしたらいいのか？

持ち帰ります。

Q. java8が部分的にサポートされましたが、StreamなどのAPIもバックポーとされる予定はあるのでしょうか？

たぶんない。3rdpartyのものを使って欲しい

Q. Bottom NavigationはDesign Support Libraryには入りますか？

リクエストが多ければ。現状は作ってない。

Q. InboxのようなFABを使ったメニューがDesign Support Libraryに入る予定はありますか？

ニーズがあれば、高い順にやります

Q. Jack & JillになったらOracleのJDKは不要になるのでしょうか？

結局他のツールのためにいるんじゃないかな？ Android Studio動かすのに必要なのでは？

Q. useLibrary 'org.apache.http.legacy'はいつまでサポートされますか？

deprecatedされる場合があれば、早くいう

Q. テスト環境しやすい環境とかありませんか？

android dash testingにサンプルだったりベストプラクティス集がある
mockito使おう

Q. MultiDexを使うとAndroid 4.0以上でしか動作しなくなりますが、Googleとしてはもう4.0より下のOSは切り捨てて欲しいといことでしょうか？

そうではない。
ゲームの文脈ではJeally beans以降で許されるのではないかという回答
debugでMultiDex, releaseでproguard使うとか

Q. VectorDrawableCompatは23.3.0で一部機能が削られたが、今後さらに削られることはあるか

一部の端末で動かなかったので一旦なしになったが、他にはそういう話はない。

Q. データセーバーはデフォルトで有効なのか？

有効ではない。ホワイトリストに追加するようなAPIもない。

Q. Play Game Servicesをゲーム以外で、とあったが、Google playでアプリのカテゴリはゲームにする必要があった記憶があるが未だにその制限はあるが

あるが、相談しだい

Q. OpenCLのサポートされる可能性はありますか？

renderscriptを使ってくれというのが公式。ただ、renderscriptを積極的におしてたエンジニアが退社したので、これからはvulkanになるかもしれない。

Q. build.gradleのDSLについて、パラメータ情報のリファレンスはどこ？

ない

Q. android.defaultConfig.nultiDexKeepProguardの設定はドキュメントにないけど、どこにあるのか？

もちかえり
