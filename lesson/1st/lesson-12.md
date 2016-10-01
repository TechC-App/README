# 第12回 iPhoneアプリ開発

## 今日やること
- 前回の復習
- UIの調整
- 非同期処理の実装
- 次回導入

### UI調整
- AutoLayout対応


### 非同期処理の実装

#### cocoapodsの準備
```bash
gem install --user-install cocoapods -v 0.32.1
```
```bash
~/.gem/ruby/2.0.0/bin/pod --version
```

#### ライブラリの使用方法
- 使いたいライブラリを見つける
- `Podfile` に追記
- `pod install`を実行
- `Podfile.lock`に導入したライブラリのバージョン情報などが書き込まれ、利用できるようになる

注: 今後は `RankingApp.xcodeproj` ではなく `RankingApp.xcworkspace`を開く

- JSONの読み込みを非同期に
- (画像の読み込みを非同期に)

### 次回導入
- 実機ビルド
- 自由編集
