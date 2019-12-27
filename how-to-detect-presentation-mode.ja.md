# プレゼンテーションモードの判定

組織においては、ソフトウェアアップデートなどを強制したい場合があります。
ソフトウェアアップデートやアプリケーションのアップデートの内容によっては、OSの再起動が必要なケースがあります。

プレゼンテーションモードを使用してエンドユーザーがプレゼンテーション中（またはカメラやマイクを使用してのオンラインMTG中）はビジネスに影響を与える可能性があるため、再起動は控えたいという要求を持っています。
そのためには、現在端末がプレゼンテーション中（またはカメラやマイクを使用してのオンラインMTG中）なのかを何かしらの手段、できればコマンドラインを使用して判定する必要があります。

我々はどのように「プレゼンテーションモード（やカメラやマイクを使用している）かの判定」ができるのでしょうか？

## Appleの回答

現在、これを行う簡単な方法はありません。必要な場合はFeature Requestを行ってください。

## 私が考えるワークアラウンド

アプリケーションごとであればプレゼンテーションモードを判定できます。

```sh
# For example, detecting presentation mode of "Microsoft PowerPoint" app
/usr/bin/lsappinfo info -only presentationmode "Microsoft PowerPoint" | /usr/bin/grep "AllHidden"
```

`UIPresentationMode`のステータスが`lsappinfo info -only presentationmode`コマンドの出力で判定できます。
