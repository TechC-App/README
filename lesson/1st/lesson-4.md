# 第4回 iPhoneアプリ開発

## 今日やること
- 前回の復習
- Swiftの基本その1
- 次回導入

### 前回の復習
- Playgroundの使い方

### Swiftの基本その1
#### 基礎文法1
- 変数
- 定数
- 型

```swift
// int x = 10;
// double y = 0.0;
// int: 型宣言 (int型の変数)

// var は変数なので値を上書きできる
var x = 10
x = 20

// let は定数なので値を上書きできない
/*
let y = 10
y = 20
*/

// Swiftは型の宣言を省略することができる
// 省略しない場合
// var z: Int = 10
var z = 10.0

// 省略できないパターン
// Float型の使いたい時
var float: Float = 10
```

```swift
// Bool 真偽値
var bool: Bool = true

// String 文字列
var string: String = "hogehoge"
// Swiftは文字列をシングルクォートで括って書けない
// string = 'hoge'

// Array 配列
var array: Array<Int> = [1, 2, 3]
// 下と同義
// var array: [Int] = [0, 1, 2]
// var array = [0, 1, 2]
array[0]

// 空配列の場合は型の定義が省略不可
var array2: [Int] = []
var array3 = [Int]()

// Dictionary 連想配列(辞書・Hash)
var dic: Dictionary = [
    "key1": "value1",
    "key2": "value2",
    "key3": "value3",
    ]
dic["key1"]

// キーを取得したい場合
for key in dic.keys {
    print(key)
}

// Set ユニークな値をとる配列
var ary = [0,1,2,0,1,2]
var set = Set<Int>()
set = [0,1,2,0,1,2]

```

#### 基礎文法2
- 演算子
- 条件分岐
- 繰り返し

```swift
// 演算子
// +-*/

var x = 10

// 基本的な演算
x + 1
x - 1
x * 2
x / 2
x % 3
// 下のような書き方はNG
// x+ 1
// x +1

// 代入を伴う演算
x += 1
x -= 1

// 定数の場合
/*
let y = 10
y + 1  // 変更した値を返すだけならOK
y += 1 // 自分自身が変更されるのはNG
*/

// Swiftで推奨されていない演算子(最新版だと利用不可)
x++
++x

// 文字列の演算
let string = "hoge" + "fuga"
"hoge\(string)fuga"
// バックスラッシュ(\)
// Opt + ¥

```

```swift
// 条件分岐・繰り返し
// if文
var x = 1

if x > 5 {
    print("hogehoge")
} else if x > 10 {
    print("fugafuga")
} else {
    print("other")
}

// for文
// 非推奨の書き方(パフォーマンスが悪い)
for var i = 0; i < 10; i++ {
    print("\(i) times.")
}

// よく書く書き方
for i in 0..<10 {
    print("\(i) times.")
}

(0..<10).forEach { i in
    print("\(i) times.")
}

// forEachは配列でも使える
let ary = ["a", "b", "c"]

ary.forEach { str in
    print(str)
}

// while
x = 10
while x > 0 {
    x -= 1
    print("x = \(x)")
    break
}

// switch
x = 10
switch x {
case 10:
    print("x = 10")
    // ※ break は不要 明示的にbreakしたくない場合 fallthrough を書く
default:
    print("default")
}

var bool = true
switch bool {
case true:
    print("true")
case false:
    print("false")
}
```

#### 補足
- 関数
- クロージャ
- Optional

```swift
// 関数
print("")
"".characters.count // 

let stride = 10.stride(to: 100, by: 5)
stride.forEach { i in
    print(i)
}

"hoge".containsString("ge")

// 関数の定義
// hoge: 関数名
// arg: 引数名
// -> Void : 返り値の型(Voidの場合省略可能)
func hoge(arg: String) -> Void {
    print("hoge\(arg)")
}

hoge("fuga")

// 引数が複数の場合
func hoge(first: String, second: String) -> Void {
}

hoge("", second: "")

// 返り値がある
func hoge() -> Int {
    return 10
}
hoge()

// デフォルト引数・オーバーロード etc.については次回
```

```swift
// クロージャ
// = 変数に格納された関数

// closure: クロージャ変数名
// (String) -> Void : クロージャ型定義
// { str ... : クロージャの中身
var closure: (String) -> Void = { str in
    print(str)
}

closure("hoge")

// 引数は複数受け取ることも可能
var closure2: (String, String) -> Void = { str1, str2 in
    print(str1 + str2)
}

closure2("a", "b")

// 既存の関数でも様々な箇所でクロージャが使われている
// 下の二つの処理は同義(forEach関数の引数にクロージャ変数を渡している)
(0..<10).forEach { i in
    print(i)
}

var forEachClosure: (Int) -> Void = { i in
    print(i)
}
(0..<10).forEach(forEachClosure)
```

#### クラス
- 列挙型
- 構造体
- クラス

### 次回導入
- Swiftの基本その2
