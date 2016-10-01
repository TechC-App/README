# 第5回 iPhoneアプリ開発

## 今日やること
- 前回の復習
- Swiftの基本その2
- 次回導入

### 前回の復習
1. for文を使い、1から100まで足す
    - append: while, forEachも使って同じように書いてみる
2. if文を使い、1から100までで5で割って1余る時は2、それ以外の時は3を足す
    - append: switch文を使って同じように書いてみる
3. 2の処理を、範囲の開始と終わりを引数で受け取り、結果を返す関数を定義する
    - append: クロージャでも同じ処理を書いてみる

```swift
// for文を使い、1から100まで足す
var x = 0
for i in 1...100 {
    x += i
}
x

// while文の場合
x = 0
var i = 1
while i <= 100 {
    x += i
    i += 1  // i++ は非推奨なので使わない
}
x

// 範囲の定義の仕方 下の二つは同じ
1..<101 // 1以上101未満
1...100 // 1以上100以下
```
```swift
// if文を使い、1から100までで5で割って1余る時は2、それ以外の時は3を足す
var x = 0
for i in 1...100 {
    if i % 5 == 1 { // 5で割って1余る時
        x += 2
    } else {
        x += 3
    }
}
x

// switchの場合
x = 0
for i in 1...100 {
    switch i % 5 {
    case 1:
        x += 2
    default:
        x += 3
    }
}
x
```
```swift
// 2の処理を、範囲の開始と終わりを引数で受け取り、結果を返す関数を定義する
func sum(start start: Int, end: Int) -> Int {
    var x = 0
    for i in start...end {
        if i % 5 == 1 {
            x += 2
        } else {
            x += 3
        }
    }
    return x
}

sum(start: 10, end: 1000)

// クロージャの場合
var closure: (start: Int, end: Int) -> Int = { start, end in
    var x = 0
    for i in start...end {
        if i % 5 == 1 {
            x += 2
        } else {
            x += 3
        }
    }
    return x
}
closure(start: 1, end: 1000)
```

### Swiftの基本その2

#### クラス
- 列挙型
- 構造体
- クラス

```swift
import UIKit

class Human {
    // プロパティ定義
    // クラス変数
    static let childAgeRange = 6...18
    
    // メンバ変数
    let age: Int
    let weight: Float
    
    // クラス関数
    static func hoge(first: Int) -> Int {
        return first
    }
    
    // メンバ関数
    func halfWeight() -> Float {
        return weight / 2
    }
    
    // イニシャライザ
    init(age: Int, weight: Float) {
        self.age = age
        self.weight = weight
    }
    // イニシャライザは複数定義可能
    init() {
        age = 10  // 変数名の被りがない時はselfを省略可能
        weight = 50.0
    }
    
}

let human = Human(age: 25, weight: 60.0)
// クラス変数呼び出し
Human.childAgeRange

// メンバ変数呼び出し
human.age
human.weight

// クラス関数呼び出し
Human.hoge(10)

// メンバ関数呼び出し
human.halfWeight()

// アクセス修飾子
/*
public    // どこからでも参照できる (デフォルト)
internal  // 同じモジュール内からのみ参照できる
private   // 同じファイル内からのみ参照できる
*/
```
```swift
class HumanClass {
    var age = 10    // プロパティ定義時に値を代入すると、それが初期値として使われる
    // すべてのプロパティに初期値があると、イニシャライザが省略可能
}
```

##### classとstructの違い
- 値渡しか参照渡しか
-- classは参照渡し
-- structは値渡し
```swift
class HumanClass {
    var age = 10
}
struct HumanStruct {
    var age = 10
}

let human1 = HumanClass()
human1.age
human1.age = 20  // classはプロパティの変更はできる
human1.age

human1 = HumanClass() // human1を直接書き換えるのは当然NG

let human2 = HumanStruct()
human2.age
human2.age = 20 // structはプロパティの変更もNG
```
- イニシャライザの定義
```swift
class HumanClass {
    let age: Int
    init(age: Int) { self.age = age } // 消すとエラー
}

struct HumanStruct {
    let age: Int
    // structは各プロパティを引数としてとるイニシャライザがデフォルトで定義される
    // ※ イニシャライザを独自に定義すると、デフォルトイニシャライザは消える
}

HumanStruct(age: 10)
```
- structは継承不可
```swift
// クラスの継承
class Human {
    let age: Int
    init(age: Int) { self.age = age }
}

class Child: Human {
    let grade: Int
    init(age: Int, grade: Int) {
        self.grade = grade
        super.init(age: age) // 親のイニシャライザは、自身のプロパティ設定後に呼ぶ必要がある
    }
}
```
```swift
// SwiftのEnum
enum Grade {
    case grade1
    case grade2
    case grade3
    case grade4
    case grade5
    case grade6
    case other
    
    // イニシャライザを定義可能
    init(age: Int) {
        switch age {
        case 6:
            self = .grade1
        case 7:
            self = .grade2
        case 8:
            self = .grade3
        case 9:
            self = .grade4
        case 10:
            self = .grade5
        case 11:
            self = .grade6
        default:
            self = .other
        }
    }
    
    // タイプメソッドなども定義可能
    static func lowerGrade() -> [Grade] {
        return [.grade1, .grade2, .grade3] // 型が自明なので Grade は省略化
    }
}

Grade.grade1
Grade.lowerGrade()
Grade(age: 10)
```
```swift
// enumとclassを組み合わせた使い方

enum Gender {
    case Male
    case Female
}

enum Grade: Int {
    case grade1 = 6
    case grade2 = 7
    case grade3 = 8
    case grade4 = 9
    case grade5 = 10
    case grade6 = 11
}

class Human {
    let age: Int
    let weight: Float
    let gender: Gender
    
    init(age: Int, weight: Float, gender: Gender) {
        self.age = age
        self.weight = weight
        self.gender = gender
    }
}

class Child: Human {
    let grade: Grade?
    
    override init(age: Int, weight: Float, gender: Gender) {
        grade = Grade(rawValue: age)
        super.init(age: age, weight: weight, gender: gender)
    }
}

let human = Human(age   : 10,
                  weight: 50,
                  gender: .Male)

let child = Child(age   : 8,
                  weight: 30,
                  gender: .Female)

human.weight
child.grade
```
#### 補足
- Optional
```swift
enum Enum: Int {
    case A = 1
    case B
}

struct Struct {
    var gender: Enum = .A
}

var s = Struct()
s.gender
s.gender = Enum(rawValue: 1)

// Optional の扱い方
// プロパティの型自体をOptionalで定義する
// 代入する時に、Optionalを外すようにする
```

### 次回導入
- 
