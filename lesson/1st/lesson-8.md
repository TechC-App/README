# 第8回 iPhoneアプリ開発

## 今日やること
- 前回の復習
- 次回導入

### 課題
- チャットメッセージ入力欄が空の時に「送信」ボタンを押せないようにする
  Hint: 
  - 送信ボタンの `UIButton` を操作できるよに、`@IBOutlet`として参照できるようにする
  - `UIBtton`の活性/非活性の状態は`UIButton#enabled`で操作可能
  - `UITextField`に変更があったことを検知するためには `UITextFieldDelegate` の
    ```swift
    func textField(textField: UITextField, shouldChangeCharactersInRange range: NSRange, replacementString string: String) -> Bool {
        // something
        return true
    }
    ```

### 利用するPodライブラリの差し替え

`Socket.IO-Client-Swift` ではなく `SwiftWebSocket` を利用するように変更

```ruby
# 既存の指定は削除(or コメントアウトして、新規追加)
# pod 'Socket.IO-Client-Swift', '~> 6.1.2' # Or latest version
pod 'SwiftWebSocket'
```

```bash
# プロジェクト直下のディレクトリで以下コマンド実行
pod install
```

### Tips
#### リポジトリ管理外にしたいファイルの設定
`.gitignore` に定義を追加
```
xcuserdata/
```
*xcuserdataには個人環境毎の設定が配置されるので、通常リポジトリ管理は不要*

#### 画面読み込み時のライフサイクル
```swift
    // 画面読み込み時に呼ばれる (基本的には1回のみ)
    override func viewDidLoad() {
        ...
    }

    // 画面が表示されるときに呼ばれる (バックグラウンドからの復帰時や、遷移先画面から戻ってきたときなど含む)
    override func viewDidAppear(animated: Bool) {
        ...
    }

    // viewWill~ もある
```

#### SwiftWebSocketの使い方
```swift
// ライブラリ利用の宣言
    import SwiftWebSocket

    override func viewDidLoad() {
        super.viewDidLoad()
        // WebSocketクラスのインスタンスを生成
        let webSocket = WebSocket()
        
        webSocket.event.open = {
            // 通信接続完了時の処理
        }
        
        webSocket.event.close = { code, reason, clean in
            // 通信切断後の処理
        }
        
        webSocket.event.error = { err in
            // 通信エラー時の処理
            print(err)
        }
        
        webSocket.event.message = { msg in
            // メッセージ受信時の処理
        }
        
        webSocket.open("http://localhost")
    }
```

### 次回導入
- 
