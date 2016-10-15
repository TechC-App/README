# 後期 第3回 iPhoneアプリ開発

## 今日やること
- 今後のアプリ制作
- 制作アプリテーマ決定に向けて
- 制作アプリ用のリポジトリ作成
- アプリ制作フロー

## 今後のアプリ制作
進め方再確認

10/15 進め方確認・テーマ決定  
~ 11/5 設計  
~ 11/26  製造(前半)  
12/3 中間発表  
~ 1/7 製造(後半)  
1/14 成果物発表  
2/11 We are TECH.C.  


## 制作アプリテーマ決定に向けて
### 便利系アプリ
- タスク管理 <= サンプルで作成予定
- フォトライブラリー
- 画像加工
- メモアプリ

### ミニゲーム
- パズル
- クイズ


## 制作アプリ用のリポジトリ作成
### 空のXcodeプロジェクトを作成
注: `Create git repository on ~`はチェックを入れておく

### Github上にリポジトリ作成
[サンプル用リポジトリ](https://github.com/TechC-App/TaskApp)

各自のリポジトリは[リポジトリの作成](https://github.com/new)からPersonal Spaceに作成  
注: `Initialize this repository with a README`にはチェックを入れないこと

### Xcodeプロジェクトのremoteに作成したリポジトリを設定
- Xcodeの`Source Control`を開く
- working copies => Configure ~ を開く
- Remotes => 「+」のAdd Remote から、作成したリポジトリを追加
- Push

#### READMEの編集
- Github上から「Add Readme」でREADME.mdを追加

[サンプルのREADME](https://raw.githubusercontent.com/TechC-App/TaskApp/master/README.md) を参考に入力

#### 作成リポジトリの共有
作成したリポジトリのURLを  
[授業リポジトリのISSUE](https://github.com/TechC-App/README/issues/1)
にコメントで追記してください  
例: https://github.com/TechC-App/README/issues/1#issuecomment-253950069

参考: [Github上でのMarkdown記法](https://guides.github.com/features/mastering-markdown/)

もし[GithubのIDと名前の対応](https://github.com/TechC-App/README/blob/gh-pages/username)に記入していない人がいれば、そちらも記入して下さい。

## アプリ制作フロー

プロジェクトの進め方は大きく分けて2つ

- ウォーターフォール型  <= 今回はこちらを採用
最初に最終的な作るものをきっちり設計し、それに従い製造、テストを進めていく

- アジャイル型 (プロトタイピングモデルが近い)  
最初の段階では作るものの大枠だけ決め、あとは動くもの(プロトタイプ)を作ってそれを触りながらブラッシュアップしていく

### 工程
#### 通常のフロー
1. 企画
  - そもそも何を作るかの検討
2. 要件定義
  - 作るアプリのターゲット
  - ユースケース
  - 画面・機能
3. 基本設計
  - 画面構成
  - 機能構成
  - システム構成
4. 詳細設計
  - クラス設計
  - モデル設計
5. 製造
  - View作成 (Storyboard)
  - Controller作成
  - Model作成
6. テスト
  - 単体テスト
  - 結合テスト
  - 受入テスト
7. リリース
  - 審査提出
  - ストア公開

#### 今回の授業のフロー
1. 企画 (10/15)
  - テーマ決め
2. 要件定義
  - 作るアプリのターゲット
  - ユースケース
  - 画面・機能
3. 設計 (~ 11/5)
  - 画面構成
  - 機能構成
  - (システム構成)
    - サーバ通信、外部システムとの連携がある場合
5. 製造
  - View作成 (Storyboard)
  - Controller作成
  - Model作成
6. テスト (~ 1/7)
  - 単体テスト
7. リリース (1/14)
  - 提出
  - (審査提出)
  - (ストア公開)
    - 希望があれば

## 再掲
今後の授業は各自の作業がメインになるので、授業時間内で解説してほしい内容や、特別取り上げてほしい題材、その他質問などあれば[質問BOX](https://github.com/TechC-App/README/issues/2)にコメントください。
（口頭で直接でも良いですが、前もって書いておいてもらった方がスムーズです）
