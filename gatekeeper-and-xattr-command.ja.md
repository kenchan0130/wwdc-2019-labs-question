# Gatekeeperとxattrコマンドについて

Gatekepperを有効にすると、App Store経由または確認済みの開発元からのアプリケーションであればインストールすることが可能です。

macOSには `xattr` コマンドが用意されています。

```sh
xattr -c xxx.app
# or
xattr -r -d com.apple.quarantine xxx.app
```

上記のコマンドを実行すると `com.apple.quarantine` のカスタム属性を取り除くことができます。

ここで問題になるのは、未署名であるアプリケーションに対して `xattr` コマンドを使用して `com.apple.quarantine` のカスタム属性を取り除くと、
Gatekepperを有効にしていても、Gatekeeperの検閲をすり抜けることができてしまいます。

そのため、構成プロファイルにてGatekepperを強制するポリシーを組織で用意したところで、その意味を成しません。


Appleではこのような事象についてどういった意見を持っているのでしょうか？
また、この問題に対する回避策はあるのでしょうか？


質問者個人としては、企業において `xattr` コマンドの抜け道を許容してしまっている点は脆弱であると考えています。

## Appleの回答

これは仕様です。ユーザーの意図で削除したのでセキュリティに脆弱であるとは言えません。
GateKeeperの有効/無効の設定を管理者のみに制限したとしても、拡張属性の削除がユーザー権限でできる点に問題を感じるのであれば[Feedback Assistant](https://feedbackassistant.apple.com/)でフィードバックとして報告してください。
