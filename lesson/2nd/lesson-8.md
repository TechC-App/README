# 後期 第８回 iPhoneアプリ開発

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
### データ永続化
#### 必要ファイルの作成
- `Data Model`定義
  - CoreDataのバックエンドで利用するSqliteに何を保存するかの定義
  - `Entity` = DBのテーブル
  - `Attribute` = テーブルのカラム
- Class定義
  - ソース上からデータを参照するための定義
  - ファイル自体はDataModelの定義を元に自動生成可能

#### CoreDataの中身の参照
CoreDataはバックエンドにSqliteを使っているので、ファイルパスさえわかれば直接参照が可能
- シミュレータのパス  
  => 以前の[講義メモ参照](https://github.com/TechC-App/README/blob/gh-pages/lesson/2nd/lesson-4.md#その他)
- sqliteファイルのパス  
```bash
# シミュレータパスに移動してから以下を実行
find ./ -name "*.sqlite" 
```  

sqliteコマンドで直接操作
```bash
# sqliteファイルパスに移動してから
sqlite3 TaskApp.sqlite
# 以下sqliteのコンソール上で実行
# テーブル一覧
.tables
# スキーマ定義一覧
.schema
# Task一覧
SELECT * FROM ZTASK;
```

### 通知機能
#### 通知表示の種類
- アラート
- バッジ
- サウンド

#### 通知方法の種類
- リモート通知
  - サーバサイドから通知を飛ばす
  - アプリ側で`device token`を取得、それをサーバ側に送信して、通知の登録を行う必要がある
  - 任意のタイミングで通知が可能
  - オンラインでないと通知が届かない
  - シミュレータで利用不可
- ローカル通知
  - アプリ内で通知を飛ばす
  - 通知のタイミングは固定 (事前の時間指定は可能)
  - オフラインでも通知可能

### 画面実装

## 再掲
今後の授業は各自の作業がメインになるので、授業時間内で解説してほしい内容や、特別取り上げてほしい題材、その他質問などあれば[質問BOX](https://github.com/TechC-App/README/issues/2)にコメントください。
（口頭で直接でも良いですが、前もって書いておいてもらった方がスムーズです）
