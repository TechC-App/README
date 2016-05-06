# 第3回 iPhoneアプリ開発

## 今日やること
- 前回の復習
- サンプルアプリを動かす
- 次回導入

### 前回の復習
- Xcodeで新規プロジェクトを作成し、シミュレータを起動してみましょう
    - EX) デバイスの種類を変えてみましょう
- Storyboardを選択し、ラベルを配置してみましょう
    - EX) ラベル以外にも、ボタンや画像を配置してみましょう
    - EX) Autolayoutを使って位置の調整をしてみましょう
- 前回使ったアプリ(https://github.com/TechC-App/SampleApp )をgithubから開き
  中身を自由に何箇所か変更してみましょう。
　また、その後編集をリセットしてみましょう。

### サンプルアプリを動かす
- FlappySwift(ゲーム)  
https://github.com/fullstackio/FlappySwift

```
// setup physics
self.physicsWorld.gravity = CGVector( dx: 0.0, dy: -1.0 )
self.physicsWorld.contactDelegate = self
        
// setup background color
skyColor = SKColor(red: 1.0/255.0, green: 12.0/255.0, blue: 20.0/255.0, alpha: 1.0)
self.backgroundColor = skyColor
```

- チャット  
https://github.com/acani/Chats
- RSSリーダ的なもの  
https://github.com/Dimillian/SwiftHN
  - ブランチはmasterを選択でOK
```
// NewsViewController.swift#165
override func tableView(tableView: UITableView, heightForRowAtIndexPath indexPath: NSIndexPath) -> CGFloat
{
    let title: NSString = (self.datasource[indexPath.row] as! Post).title!
    // return NewsCell.heightForText(title, bounds: self.tableView.bounds)
    return 50
}
```
- PinterestっぽいUIのアプリ
https://github.com/demonnico/PinterestSwift

#### Tips
- Cmd+Rでビルド
- ターミナル.appの起動
    - Finder: アプリケーション > ユーティリティ > ターミナル
    - DashBoard: その他 > ターミナル
- コマンドでのリポジトリのclone方法
```
# ドキュメントディレクトリに移動
cd ~/Documents
# 念のため同名ディレクトリ削除
rm -rf SwiftHN
# clone
git clone --recursive https://github.com/Dimillian/SwiftHN
# clone先のディレクトリに移動
cd SwiftHN
# プロジェクトファイルをXcodeで開く
open SwiftHN.xcodeproj
```
- Cmd + Shift + O
    - クイックサーチ

### 次回導入
- Playgroundの使い方
- Swift文法基礎

```
var num = 5

(1...100).forEach { _ in
    if num % 5 == 0 {
        num += 2
    } else {
        num += 1
    }
}

num
```

### 授業アンケート
https://docs.google.com/forms/d/19umzqyL81uvZ-bPLm1asvHbmBenhPxRrS_qqpPAm1UI/
