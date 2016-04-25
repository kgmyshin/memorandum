江川 崇

- 複数バージョンの共存
- Android Studio 2.0
- Android Studio 2.1


## 複数バージョンの共存

複数のバージョンを共存することが可能

/Applications/
  Android Studio.app
  Android Studio Canary.app

~/Library/Preferenecs/AndroidStudio 2.0
~/Library/Preferenecs/AndroidStudioPreview 2.1


ツールのバージョン追従の考え方

- いきなり実戦の全部隊のバージョンを全て一世にあげるのは難しい。
- だがあげるタイミングを逃すとずっとふるいままになる

- 誰かがなるべくCanaryやDevに並行して触れておく
- 適切だと思ったらみんなに展開する

今(2016/04/25)だと
- compileSdkVersion, buildToolsVersionは23系
- Gradleは2.4以上(2.8が理想)　pluginは2.0系
- targetSdkVersionはゆっくりとテストしてからあげる


Gradle plugin 2.0.0を適用
- Andoird Studio 2.0で古いプロジェクトをビルドするとダイアログがでるのでそこでUpdateする

SDKのインストールディレクトリについて
- 基本的には併用しても大きな問題はない
- いくつか新しい実験用バージョンに引きずられるものがあるので注意

新しいエミュレーターができた
- 実機より早い、サクサク動く
- UI(Embded Control)が見直された
- 電話をかけるなどが簡単にできる
- SmSを簡単に遅れる
- バッテリーの量をプログレスバーで変えられる
- apkをドラッグアンドドロップしてinstallできる
- vector assets studio(プリセットのsvgを追加できる)

## Andriod Studio 2.1について

Android N Developer Previewのサポート

- java8の機能のランタイムサポート(一部のみ)
- lamdaについてツールチェインが下位互換サポート
- jdk8必須
- jack and jill 必須


Jack and jill => .classファイルにする工程がない

Android Studio 2.1(beta)の問題
- gitのインテグレーション機能が上手く動かない
- Android N Preview系でのデバッグ実行に問題がある
- 明示的にIPv6してしなければならない
- Nはこれなので正式なツールチェイン(やく1年後)


http://bandroid.com
"Android Studio Bug"のテンプレートであげると良い

## Android Sutiod 2.0

DEXに関する処理の改善による高速化

- build tools 23.0.2から、Gradle 2.4(Plugin 2.0.0)以降から
- dexInProcessをtrueにするとその処理が適用される(Android Studio2.0ではデフォルトでtrue)
- 依存関係が15-20個程度で2倍て早くなる


## DEX生成時のメモリ不足の対策

いままで

build.gradle
```
android {
    dexOptions {
        javaMaxHeapSize "2g"
    }
}
```

これから。(今までの方法は使えるなくなる)

gradle.properties

```
org.gradle.jvmargs=-Xmx4094m
```

シュリンク昨日

不要メソッドを消したい(主に64k問題回避)
- Proguardは単一のjar = フルのDEX化が必要
遅いのでデバッグbルドで使うには非現実

```
android {
    buildTypes {
        debug {
            minifyEnabled true
            useProguard false
        }
        relsease {
            minifyEnabled true
            useProguard true
        }
    }
}
```

ADBによるデプロイ高速化

platform tools 23.1より
従来の5倍の速さ


AAPTにきのう 追加

接続中のデバイスに必要な
接続中デバイスに特化したパッケージの生成(andorid Sutdio経由でdebugするときのみ)


Instant Runについて

接続中のでばいすに対する2回目以降のアップデートインストールを高速化する仕組み
- 継続して接続中であること
- デバッグビルドであること
- APIレベル16位以上
