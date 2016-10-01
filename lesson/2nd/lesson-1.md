# 後期 第1回 iPhoneアプリ開発

## 今日やること
- 後期授業概要の説明
- 前提知識の確認

## 後期授業概要の説明


## 前提知識の確認
### Github
- 後期のアプリ制作もGithub上のリポジトリでやりとりすることになる。テーマの決定などにも利用するので、アカウント作成必須
  - 前期試験を受けていない/後から受けた人はアカウント名を連絡ください。
- CI環境
  - リモート環境でアプリのデプロイをするために利用
  - メジャーなものとしてJenkinsがあるが、本授業ではiOSアプリのビルド、配信をするという性質上、別のツールを利用予定(仮)

#### 参考: OSXのローカルでJenkinsセットアップ
- https://jenkins.io/ からJenkinsのパッケージをDL
  - https://jenkins.io/content/thank-you-downloading-os-x-installer/#stable  
  (学校のMacではインストール不可)


## 自由に利用できるサーバ環境
ログイン
IP: 150.95.131.101  
ユーザ名: member  
秘密鍵:  https://drive.google.com/open?id=0Bz34Lh0Zaqg5ejh1OEphaGJ4OEE

1. リンクから秘密鍵を落としてもらい、それを任意の場所に配置  
  (`~/.ssh/id_rsa`に配置するとデフォルトの鍵として利用される)
2. 配置した鍵のパーミッションを変更  
  `chmod 600 [秘密鍵のpath]`
3. ログイン  
  `ssh -i [秘密鍵のpath] member@150.95.131.101`

- Jenkins  
  http://150.95.131.101/  
  ログイン情報: サーバ上の `/home/member/jenkins.conf` に記載

- AppleDeveloperProgramアカウント  
  - 発行され次第共有

## 今後のコミュニケーション手段
基本的に[GitHubのIssue](https://github.com/TechC-App/README/issues)上で行う予定。

授業内外での質問があればまとめて[質問BOX](https://github.com/TechC-App/README/issues/2)まで。

## 次回について
第二回授業では、前期に学習した内容の復習を予定。

特に取り上げて欲しい題材があれば、これも[質問BOX](https://github.com/TechC-App/README/issues/2) までコメントください。
