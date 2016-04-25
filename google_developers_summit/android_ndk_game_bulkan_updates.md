松田白朗

Android
プラットフォーム・アップデート(ゲーム編)

1. Android N Developer Preview
2. Android NDK
3. Google Play, 開発ツール
4. Vulkan

## Android N Developer Preview

ゲーム開発に役立つ機能
- バッテリ性能、パフォーマンス向上
- Notificationバンドル、カスタマイズ
- Vulkan & Open GL ES3.2

挙動の変更
- データ・セーバ
- 新しいセキュリティ
- 低メモリデバイスへの対応

## Notification

Notificationの統合、コントロールの追加

## 挙動の変更

- バックグラウンドの挙動
  - データ・セーバ
    ConnectivityManagerの設定をチェック
  - JobScheduler,GCMなどのシステムサービスに以降
- 低メモリデバイスへの対応
  - メモリ。フットプリトに注意
    - 圧縮テクスチャの使用
- アタr強いセキュリティ
  - /system/libいかの未公開ライブラリの参照が禁止に
  - libpng, libcryptなど

## Vulkan対応

- DP2 OTAで対応 Nexus6P/5X
- Android Beta Programにサインアップ

今後対応
- NexusPlayer, Nexus9
- OEM独自対応 - API Level23
  Galaxy S7, nVidia Shield TV & Tablet


# Android NDK

## NDKr11c

- Clangがデフォルトコンパイラに(gccはdeprecated)
- SDKマネージャからダウンロード
- 開発はAOSP上で
- バグ報告はgithub上で
  github.com/android-ndk/ndk

## NDKr12 Beta
- Vulkan.h/ Vulkan.so追加
- Vulkanサポートツール追加
  - glslc
  libShaderc
  Validation layer
- githubからダウンロード

ndkはこれから5週間に一度ベータリリース、1Qに1度正式リリースを

# google play, 開発ツールについて

## Gamer ID, アバター
- 自動サイン・イン
- IDトアバターヲユーザーガシテイ
- アプリ側変更はほとんどなし


## Cardboard SDK 3DオーディオAPI

VRゲーム対応の3Dオーディオ音源対応
- HRTF処理
- モノラル音源、アンビエント音源対応
- 別スレッドでオーディオ処理

## Android Studio
よりよりNDKサポート

- lldbを使った安定デバッグ
- adb高速化
- gradleでのc++コンパイル
- GPUデバッガ

# Vulkan

## 次世代高速汎用描画API : Vulkan
- よりよいパフォーマンス、バッテリー来rふ
- コマンドバッファのマルチスレッド生成
- オフラインシェーンパイル
- アプリケーション側での正確なメモリ管理
- モバイルHW機能に積極的

## AndroidのVulkan対応

- 対応デバイス
  HW要件: OpenGL ES3.1 AEP相当
  ようドライバ対応
  現実的にはOpenGLとの両対応が必要
- APIのダイナミックロード推奨
  APIlevel23以前でも動作するように
  vulkan_wrapper.cpp/h
