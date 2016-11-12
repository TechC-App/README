# 後期 第７回 iPhoneアプリ開発

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

## 制作アプリ製造
### データの永続化
#### `NSUserDefaults`
- 実態としてはplist(XML)
- なんらかの設定値など、簡易的に値を永続化したい場合に便利
- 値の検索、複数項目の同時操作のようなものには向かない

#### `CoreData`
- 実態としてはSQLite
- MySQLなどと同じDBMiddleWareなので複雑なデータ管理が可能
- 外部ライブラリなしでDB扱うとしたら一択
  - iOSのCore機能を比較的低レイヤーで触ることがあるので、若干難易度が高い

--- 外部ライブラリ利用前提 ---

#### [MagicalRecord](https://github.com/magicalpanda/MagicalRecord)
- `CoreData`ラッパー

#### [Realm Swift](https://realm.io/docs/swift/latest/)
- 比較的最近出てきたDBライブラリである`Realm`をSwiftから扱うためのライブラリ
- Swiftでアプリ内DBを扱う場合はデファクトになりつつある

### 補足
#### ライブラリ管理について
Swiftで利用するライブラリを管理するマネージャとしては主に
- Cocoapods
- Carthage

の2種類がメジャー。

本授業の中では基本的にはCocoapodsを利用する。

#### 学校のマシンでのライブラリマネージャ導入手順
##### homebrew
- インストール
```bash
cd
mkdir homebrew
curl -L https://github.com/Homebrew/homebrew/tarball/master | tar xz --strip 1 -C homebrew
```
- `PATH`を変更
```bash
echo 'export PATH=/Users/student/homebrew/bin:$PATH' >> ~/.bash_profile
source ~/.bash_profile
```
- 動作の確認
```bash
brew update
```

##### cocoapods
- rubyのインストール
```bash
brew install ruby
```
- gemのインストール
```bash
gem install cocoapods
```

##### carthage *require Xcode 7.3*
```bash
brew install carthage # require Xcode 7.3
```


## 再掲
今後の授業は各自の作業がメインになるので、授業時間内で解説してほしい内容や、特別取り上げてほしい題材、その他質問などあれば[質問BOX](https://github.com/TechC-App/README/issues/2)にコメントください。
（口頭で直接でも良いですが、前もって書いておいてもらった方がスムーズです）
