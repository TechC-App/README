# 後期 第9回 iPhoneアプリ開発

## 今日やること
- リマインド
- 制作アプリ製造

## リマインド
### 作業リポジトリの共有
各自、自分のリポジトリを作成したら [後期制作アプリテーマの決定](https://github.com/TechC-App/README/issues/1) までコメントで共有してください。

### スケジュール再確認
10/15 進め方確認・テーマ決定  
~ 11/5 設計  
~ 11/26  製造(前半)  
12/3 中間発表  
~ 1/7 製造(後半)  
1/14 成果物発表  
2/11 We are TECH.C.  

### 中間発表について
中間発表では、各自の進捗をこちらの手元で確認させてもらいます。  
※ みんなの前で発表したりはしません

#### Must
1. [後期制作アプリテーマの決定](https://github.com/TechC-App/README/issues/1)に自分のリポジトリのURLを貼る
2. READMEにアプリの概要、仕様がまとめられていること  
  (最低限、[TaskApp](https://github.com/TechC-App/TaskApp)と同じ内容の記載があること)

#### Want
現在実装部分のソースコードをpushしていること

## 制作アプリ製造
### タスク一覧画面実装
#### セルへの場所・期限の表示追加
 - セルの表示をカスタマイズするために、`CustomCell`を追加
#### 完了ボタンの追加

#### 詳細画面への遷移
画面遷移の種類
- モーダルで現在画面の上に表示  
```swift
let viewController = TaskDetailViewController()
presentViewController(viewController, animated: true, completion: nil)
```
- ナビゲーションコントローラを使って、次の画面として遷移
```swift
let viewController = UIStoryboard(name: "Main", bundle: NSBundle.mainBundle()).instantiateViewControllerWithIdentifier("TaskDetailViewController")
navigationController?.pushViewController(viewController, animated: true)
```

### タスク詳細画面実装
Optional判定後に、その値を利用した処理が入る場合

```swift
// 通常の`nil`判定を利用する場合
if task != nil {
    // `task`は`nil`でないことがわかっているはずなのに、unwrapしてあげないといけない
    titleField.text = task?.title
    ...
}

// `if let`を利用する場合
if let unwrappedTask = task {
    // ここには`task`に値がある場合のみ入り、かつUnwrapされた結果が`unwrappedTask`に代入される
    titleField.text = unwrappedTask.title
    ...
}

// `guard let`を利用する場合
guard let unwrappedTask = task else {
    return
}
titleField.text = unwrappedTask.title
...
```


## Tips
### プロジェクトファイル階層と実ファイル階層の同期
[`synx`](https://github.com/venmo/synx)
`gem install synx` もしくは、`Gemfile` に追加して `bundle install` で入れる

### StoryboardからViewControllerを生成
```swift
// `NSBundle`を利用する場合は、基本`mainBundle()`
let bundle = NSBundle.mainBundle()
let storyboard = UIStoryboard(name: "Main", bundle: bundle)
// Storyboard上で設定している`Storyboard ID`を元に、対象のViewControllerを呼び出す
let viewController = storyboard.instantiateViewControllerWithIdentifier("TaskDetailViewController")
```
上記を簡単に参照できるようになる`R.swift`というライブラリもあるので、一度やり方を覚えたらそちらを利用するのを推奨

### TableViewのセルの再描画
これまでは基本`reloadData()`を利用していたが、これはTableViewの全セルを読み込み直す。  
再描画が必要なセル数が少ない場合は`tableView.reloadRowsAtIndexPaths(indexPaths:, withRowAnimation:)`を利用すると良い。

### guard
以下は等価
```swift
if [条件] {
    [条件を満たす場合の処理]
} else {
    [条件を満たさない場合の処理]
}
```
```swift
guard [条件] else {
    [条件を満たさない場合の処理]
    return
}
[条件を満たす場合の処理]
```

### UIViewControllerのライフサイクル
http://qiita.com/motokiee/items/0ca628b4cc74c8c5599d

## 再掲
今後の授業は各自の作業がメインになるので、授業時間内で解説してほしい内容や、特別取り上げてほしい題材、その他質問などあれば[質問BOX](https://github.com/TechC-App/README/issues/2)にコメントください。
（口頭で直接でも良いですが、前もって書いておいてもらった方がスムーズです）
