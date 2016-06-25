# 第10回 iPhoneアプリ開発

## 今日やること
- 前回の復習
- UIの調整
- 個別アプリの詳細画面の表示
- 次回導入

### 使い方画面の追加
#### 方針
1. 使い方画面用のViewControllerを追加する
2. トップ画面に、ボタンを追加する
3. 2で追加したボタンから、1で追加したViewControllerへのsegueを設定する
4. 遷移ができたら、使い方画面の中身を好みで作り込む



#### セルをタップした時のDelegateメソッド
```swift
    override func tableView(tableView: UITableView, didSelectRowAtIndexPath indexPath: NSIndexPath) {
        // タップした時の処理
    }
```

### 個別アプリの詳細画面の追加
`RankingDetailViewController.swift`ファイルを新規で追加し、
その中で `RankingDetailViewController` クラスの定義を書く

#### 詳細画面への遷移
```swift
        // ランキング詳細画面のインスタンスを生成

        // `NSBundle.mainBundle()`は現時点では決まり文句として覚えておけばOK
        let storyBoard = UIStoryboard(name: "Main", bundle: NSBundle.mainBundle())
        // Storyboard上から、IDをキーにしてViewControllerを生成
        let viewController = storyBoard.instantiateViewControllerWithIdentifier("RankingDetailViewController")
        
        // 独立した画面としてModal表示
        // self.presentViewController(viewController, animated: true, completion: nil)

        // NavigationController配下の画面として遷移
        self.navigationController?.pushViewController(viewController, animated: true)
```

#### Tips
ソースコード上でNavigationController配下にViewControllerを追加する場合、Storyboard上でNavigationBarが表示されないので実際の表示がわかりにくい。
その場合、StatusBarとNavagationBarの高さ(20 + 44)分のUIViewをhiddenで配置することで、NavagationBarが表示される領域を確認しながらStoryboard上の操作ができる。

#### JSONのパース
##### JQの導入手順
1. https://github.com/stedolan/jq/releases/download/jq-1.5/jq-osx-amd64 をダウンロード
2. ダウンロード後、 `jq-osx-amd64` => `jq` にリネーム
3. ターミナル.app を起動
4. `cd ~/Downloads/` でダウンロードしたディレクトリに移動
5. `chmod 755 jq` でファイルに実行権限をつける
6. `./jq` でエラーにならないことを確認

##### JQの使い方
JSONの情報をそのまま整形して表示
```bash
curl 'https://itunes.apple.com/jp/rss/topfreeapplications/limit=10/json' | ./jq .
```
レスポンスに含まれるアプリのタイトルのみ表示
```bash
curl 'https://itunes.apple.com/jp/rss/topfreeapplications/limit=10/json'| jq '.feed.entry[].title.label'
```
レスポンスに含まれるアプリの個数を確認
```bash
curl 'https://itunes.apple.com/jp/rss/topfreeapplications/limit=10/json' | ./jq '.feed.entry | length'
```


#### 詳細画面に表示する情報の決定
- アプリ名
- アプリアイコン
- 説明文
- ストアへのリンク
- 作成者
- カテゴリ
- リリース日

Itemに追加されるプロパティ
```swift
    /// 説明文
    let description: String
    /// ストアへのリンク
    let linkUrl: NSURL
    /// 作成者
    let author: String
    /// カテゴリ
    let category: String
    /// リリース日
    let releaseDate: String
```
イニシャライザに追加が必要な初期化処理
```swift
// 説明文
description = json["summary"]["label"].stringValue
        
// ストアへのリンク
urlStr = json["link"]["attributes"]["href"].stringValue
linkUrl = NSURL(string: urlStr)!
```

### 次回導入
