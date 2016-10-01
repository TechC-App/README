# 第14回 iPhoneアプリ開発

## 今日やること
- リポジトリFork確認
- テスト前の復習
- テスト

### リポジトリFork確認
- GitHubのアカウント準備
- https://github.com/TechC-App/RankingApp のリポジトリをFork
  右上の「Fork」ボタンを押下ouka
- Forkしたプロジェクトファイルを開く
  - Xcodeを起動
  - 「Checkout an existing project」を選択
  - 「Or enter a repository location」に*自分の*リポジトリURLを入力してnext
  - 正常にプロジェクトが開くことを確認
- 修正したプロジェクトをプッシュ
  - 任意のファイルを修正
  - 「Source Control」 => 「Commit」を選択
  - commitメッセージを入力し、「Push to remote」にチェックを入れた上でcommit
  - User Name/Passwordの入力ができたら、自分のGitHubのアカウント情報を入れて「OK」
- 上記手順でプッシュできていない場合
  - 「Source Control」 => 「Push」を選択
  -  User Name/Passwordの入力ができたら、自分のGitHubのアカウント情報を入れて「OK」

#### GitHubユーザ名と名前の対応記入
- 前提
GitHubから、登録メールアドレスに「student」チームへの招待メールが届いているのでそこからJoinする

https://github.com/TechC-App/README/blob/gh-pages/username
の、自分のGitHubユーザ名の横に名前を記入して保存

### テスト前の復習
- StoryboardとViewControllerの項目紐付け
- AutoLayout

### テスト
- テスト用リポジトリ  
https://github.com/TechC-App/ExaminationApp

- タイムスケジュール  
10:40 開始  
11:10 以降途中退室可  
12:05 終了

- QA
  - Q. テスト中のネット利用は可能か？
    - A. 可能
  - Q. 計算結果について、小数点以下を考慮する必要があるか？
    - A. 考慮する必要なし(小数点以下は切り捨てでOK)
