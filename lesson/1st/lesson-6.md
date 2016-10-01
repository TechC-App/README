# 第6回 iPhoneアプリ開発

## 今日やること
- 前回の復習
- 次回導入

### 前回の復習
1. 体重(Float)と身長(Float)をプロパティにもち、
　BMIを計算するメソッドを持つ`Human`クラスをつくってください
  ※ BMI: 体重 / (身長)^2
2. 1年生から6年生までの学年を表す列挙型`Grade`と、その学年をプロパティとして持つ`Human`クラスを継承した`Child`クラスを作ってください


```swift
class Human {
    let weight: Double
    let height: Double
    
    func bmi() -> Double {
        return weight / (height * height)
    }
    
    init(weight: Double, height: Double) {
        self.weight = weight
        self.height = height
    }

    // 補足: 計算型プロパティ
    var calcBmi: Double {
        return bmi()
    }
}

let human = Human(weight: 50, height: 1.5)
human.bmi()
human.calcBmi // 計算型プロパティは`()`不要
```

```swift
enum Grade: Int {
    case grade1 = 6
    case grade2
    case grade3
    case grade4
    case grade5
    case grade6
}

class Child: Human {
    var grade: Grade = .grade1
}

let child = Child()
child.weight = 40
child.height = 120
child.grade = Grade(rawValue: 10)!

child.bmi()
```

### チャットアプリの作成1

#### 画面サイズの変更
- iPhone4Sに合わせる場合
width: 320  
height: 480

#### 新規ファイル追加
```swift
import UIKit

class ChatViewController: UIViewController {
    
}
```

#### UITableViewDataSource用のコード追加
```swift
// DataSourceの中身を定義するために、UITableViewDataSourceに適合させる
extension ChatViewController: UITableViewDataSource {
    
    // テーブルのセクション毎の行数を定義
    func tableView(tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        // 一旦固定で10行にする
        return 10
    }
    
    // セル毎のオブジェクトを返す
    func tableView(tableView: UITableView, cellForRowAtIndexPath indexPath: NSIndexPath) -> UITableViewCell {
        
        let cell = UITableViewCell(style: .Default, reuseIdentifier: "chatCell")
        cell.textLabel?.text = "test"
        
        return cell
    }
}
```

### 次回導入
- 
