# 第7回 iPhoneアプリ開発

## 今日やること
- 前回の復習
- 次回導入

### 前回の復習

### Tips
#### GitのリポジトリのTagの切り替え
1. ターミナル.app を起動する (アプリケーション一覧のその他の中)
2. プロジェクトのあるディレクトリに移動する
例) プロジェクトのディレクトリが `~/Documents/ChatApp` の場合
```
cd ~/Documents/ChatApp
```
3. リポジトリの状態を最新化
```
git fetch
```
3. Tagのリストを確認
```
git tag -l
```
4. Tagの切り替え
```
git checkout [Tag名]
```


### チャットアプリの作成2

#### TableViewの表示位置の変更
```swift
        // テーブルに表示されている行数を取得
        let rowCount = tableView.numberOfRowsInSection(0) // セクションは1個固定なので0指定で良い
        // 表示される行数 = メッセージの数なので以下でもOK
        // let rowCount = messageList.count
        
        let indexPath = NSIndexPath(forRow: rowCount - 1, inSection: 0)
        tableView.scrollToRowAtIndexPath(indexPath, atScrollPosition: .Bottom, animated: true)
```

#### メッセージ入力欄のクリア
```swift
textField.text = ""
```

#### 遷移した画面から戻る動作を実装
ViewController.swift に以下を追加定義
```swift
    @IBAction func firstViewReturnActionForSegue(segue: UIStoryboardSegue) {
        // anything
    }
```

### ライブラリの管理方法
#### cocoapods
https://cocoapods.org/

### 次回導入
- 実際にメッセージをサーバとやり取りできるようにする
