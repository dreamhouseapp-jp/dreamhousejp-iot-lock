DreamHouse ロック
---------------

このサンプルアプリを使用すると、DreamHouse アプリから [Lockitron 社のロック](https://lockitron.com/)を簡単に制御できるようになります。デモをご覧ください。

[![Demo](http://img.youtube.com/vi/GHIhTDFI_OY/0.jpg)](http://www.youtube.com/watch?v=GHIhTDFI_OY)

まず初めに、Lockitron Bolt と、Bolt をインターネットに接続するためのブリッジデバイスが必要です。

セットアップ：

1. Bolt およびブリッジをセットアップします。
1. API 連携アプリを新しく作成します（[https://api.lockitron.com/](https://api.lockitron.com/)）。
1. 新しく作成したアプリからテスト用のアクセストークンをコピーします。
1. [Lockitron ダッシュボード](https://lockitron.com/dashboard)にアクセスしてロックの ID を取得します。それには、ロックを選択して URL から ID をコピーします。

        https://lockitron.com/dashboard/<ここがロックの ID になります>

ローカルで実行：

1. アプリを dev モードで実行します。
`LOCK=<ロック ID> ACCESS_TOKEN=<アクセストークン> npm run dev`
1. ロックのスイッチを切り替えます。
`http://localhost:5000/toggle`

Heroku で実行：

1. アプリをデプロイします。[![Deploy on Heroku](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy)
1. ロックのスイッチを切り替えます。
`http://<Heroku アプリ>.herokuapp.com/toggle`


### アプリのアーキテクチャ

このアプリは、Lockitron API でロックの開閉を切り替えるための単純なプロキシです。デモ用にロック ID とアクセストークンをカプセル化しています。実際の環境で使用するアプリでは、OAuth を使用して API アクセスを管理する方が好ましいでしょう。このアプリのソースは、`server.js` ファイルにあります。このアプリは Node.js と Express で作成されており、リクエストを処理して、Lockitron API を呼び出し、指定されたアクションを実行します。
