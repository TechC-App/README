# 第9回 iPhoneアプリ開発

## 今日やること
- 前回の復習
- 次回導入

### ランキングアプリの作成
https://github.com/TechC-App/RankingApp

#### NavigationControllerの利用

#### ランキング一覧用ViewControllerの追加
RankingListViewController.swift をプロジェクトに追加し、ファイルの中身に
```swift
import UIKit

class RankingListViewController: UITableViewController {
    
}

extension RankingListViewController {
    override func tableView(tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        
        return 10
    }
    
    override func tableView(tableView: UITableView, cellForRowAtIndexPath indexPath: NSIndexPath) -> UITableViewCell {
        
        let cell = UITableViewCell()
        cell.textLabel?.text = "test"
        
        return cell
    }
}
```
を記述

#### ランキング情報の取得
https://rss.itunes.apple.com/?at=
から必要なデータのURLを作成

※ デフォルトでXMLのURLが作成されるが、アプリで使うときはJSON形式の方が便利なので、そちらにする
https://itunes.apple.com/jp/rss/newfreeapplications/limit=100/json

データの取得や、その情報のパースなどの画面に直接関係ない処理はViewControllerには書きたくないので、別ファイル/クラスを作る

```swift
import Foundation

class Feed {
    // ランキングの情報を取得するためのメソッド
    // 一旦、アプリ名だけを返す
    static func getRanking() -> [String] {
        // TODO: URLからの取得
        return [
            "A",
            "B",
            "C",
        ]
    }
}
```

#### throws について
今回利用する`JSONObjectWithData`のように、`throws`が付いているメソッドは処理中にエラーが発生した場合などに例外がthrowされる
```swift
public class func JSONObjectWithData(data: NSData, options opt: NSJSONReadingOptions) throws -> AnyObject
```
本来、throwされた場合の処理を出し分けて書かないといけないが、授業中は処理簡略化のため`try!`で省略する(万が一throwされた場合はアプリクラッシュする)

#### AntObjectの汎用参照クラス
```swift
// JSONデータの参照を簡略化させるための汎用クラス
class Object {
    let data: AnyObject
    
    init(_ data: AnyObject) {
        self.data = data
    }
    subscript (index: Int) -> Object {
        return Object((data as! Array)[index])
    }
    subscript (index: String) -> Object {
        return Object((data as! Dictionary)[index]!)
    }
    var arrayValue: [Object] {
        return (data as! Array).map { Object($0) }
    }
    var stringValue: String {
        return data as! String
    }
}
```

### 次回導入
- UIの調整
- 個別アプリの詳細画面の表示
