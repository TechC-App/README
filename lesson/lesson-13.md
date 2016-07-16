# 第13回 iPhoneアプリ開発

## 今日やること
- 自由編集
- 実機ビルド
- Cocoapods導入
- 次回導入

### 自由編集
ここまでの授業で作成したアプリを、各自で自由に修正してみてください。

#### 修正箇所例
- トップ画面・使い方画面
    - 背景色・画像を変える
- 使い方画面
    - 編集を不可にする
    - 説明文を追加する
- ランキング一覧画面
    - セルに表示する項目の追加
- ランキング詳細画面
    - 項目の配置変更
- etc.

#### PickUp
##### 画像の表示
使いたい画像の追加は、プロジェクト配下にある `Assets.xcassets` にDrag & DropでOK

### Cocoapods導入
#### Homebrewのインストール
権限上、`/usr` 配下にはインストールできないので下記コマンドを実行
```bash
cd
mkdir homebrew
curl -L https://github.com/Homebrew/homebrew/tarball/master | tar xz --strip 1 -C homebrew
```
環境変数の設定
```bash
touch ~/.bash_profile
open ~/.bash_profile
```
で開いたファイルに下の1行を追加
```bash
export PATH="$HOME/homebrew/bin:$PATH"
```
設定ファイルの再読み込み
```bash
source ~/.bash_profile
```

#### Cocoapodsインストール
```bash
brew update
brew install cocoapods
pod --help
```

#### ライブラリの追加方法
- 使いたいライブラリを見つける
- `Podfile` に追記
- `pod install`を実行
- `Podfile.lock`に導入したライブラリのバージョン情報などが書き込まれ、利用できるようになる

### 次回導入
