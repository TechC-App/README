# 後期 第１２回 iPhoneアプリ開発

## 今日やること
- リマインド
- 各自制作状況確認
- 実機インストール
- アプリ製造続き (時間があれば)

## リマインド
### 作業リポジトリの共有
各自、自分のリポジトリを作成したら [後期制作アプリテーマの決定](https://github.com/TechC-App/README/issues/1) までコメントで共有してください。

### 今後のスケジュール
~ 1/7 製造(後半)  
1/14 成果物発表  
2/11 We are TECH.C.  

## 各自制作状況確認

## 実機インストール
### 前提設定
#### [Apple Developer Center](https://developer.apple.com/)に登録
実機インストールするには、アプリの登録/証明書の発行などが必要だが、そのためにはApple Developer Centerに登録が必要。

共有の証明書を利用しても良いが、自分で設定などしたい場合は学校アカウントに招待するので  
http://techc-app.github.io/socrates/?#XzwokhG/write  
に、メールアドレスの記入をお願いします。  
(後で消します)

#### 証明書の発行/インストール
- `iOS App Development` を選択
- 記載されている手順を元に、CSRを発行
- アップロード
- 発行された証明書をダウンロードし、ダブルクリックでインストール

#### AppIDの登録
※ ワイルドカードを利用すれば省略可能

#### Deviceの登録
- Xcode上部メニューの Window > Devices から、接続している端末のUDIDを確認
- そのIDを登録

#### Provisioning Profileの登録/インストール
上で設定した 証明書 x AppID x Device の組み合わせを指定して、その環境でインストールするための設定を作る
- iOS App Development
- ワイルドカードのAppIDのいずれかを選択
- 上で作成した証明書を選択
- インストール対象のデバイスを選択 (基本全部でOK)
- 登録されたProvisioning Profileをダウンロードし、ダブルクリックでインストール

#### Xcodeでアカウント設定
※ 証明書/Provisioning Profileのインストールができていれば省略可能
- Xcode上部メニューの Xcode > Preferences > Accounts
- 左下の「＋」から「Add Apple ID」を選択し、アカウント情報を入力
- Provisioning Profilesの同期

#### プロジェクト設定を変更
- プロジェクト設定の Build Settings > Code Signing
- Code Signing Identity で、作成した証明書を選択
- Provisioning Profile で、作成したProvisioning Profile を選択

### ローカルインストール
iPhoneをUSBで接続して、Xcodeでビルドしたものを直接インストールする。

#### メリット
- 手元でインストールができる
- デバッグが可能

#### デメリット
- インストールできる端末のOSバージョンがXcodeに依存する
- 手元にある端末にしか入れられない

#### 手順
- 対象の端末をUSBで接続する
- Xcodeのビルド対象デバイス選択から、対象端末を選択する  
  (シミュレータの一覧の上部に表示される)
- ビルド実行

### Deploygate配信
[Deploygate](https://deploygate.com)を利用して、クラウド経由でアプリのインストールを行う

#### メリット
- リモートでインストールができる
- ビルドしたXcodeが対応していないOSバージョンにもインストールできる  
  (※ Deployment Target以下には入れられない)

#### デメリット
- デバッグができない
- バイナリをアップロードする必要があるので、若干煩雑

#### 手順
- AdHoc用にXcodeでビルド  
  Xcode上部メニューの Product > Archive からArchive
- Archive画面右メニューの Export > Save for Ad Hoc Deployment
- 対象デバイスやビルド設定などはそのままでExport
- 出力されたIPAファイルをDeploygateにアップロード
- 対象のデバイスからDeploygateにアクセスし、直接アプリをインストール

#### 参考アプリの配信ページ
https://dply.me/dqtz32

### アプリ製造続き
#### SideMenuライブラリの導入
最新はXcode8 / Swift3前提になっているので、最新のREADMEは参考にならないことが多い。

CocoaPods/Carthageに対応しているライブラリは以前のバージョンもタグなどで切られているはずなので、当時のREADMEなどを見るようにする必要がある。  
(SideMenuの場合は https://github.com/Yalantis/Side-Menu.iOS/tree/1.2.1 など)

## 再掲
今後の授業は各自の作業がメインになるので、授業時間内で解説してほしい内容や、特別取り上げてほしい題材、その他質問などあれば[質問BOX](https://github.com/TechC-App/README/issues/2)にコメントください。  
（口頭で直接でも良いですが、前もって書いておいてもらった方がスムーズです）
