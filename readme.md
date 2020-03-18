==============
![FAD0DA04-EA7A-4416-8C11-1B14A54AE4DB](https://user-images.githubusercontent.com/60056670/76921655-e543ae80-6911-11ea-85d4-7524d1fe82b5.jpeg)
==============
## ・仕様
Connpass APIから情報を取得し、LINE上に表示する勉強会検索用のLINEBOT。
LINE Messaging APIの仕様上限である10件までの情報を取得。表示する優先度は更新順。
## ・導入手順
## 1. LINE Devlopersアカウントを取得
アカウントを[作成](https://business.line.me)する。

## 2. LINE Developersに移動し、アクセストークン等を発行

チャネル基本設定画面でチャネルシークレットを発行し、Messaging API設定画面でチャネルアクセストークンを発行する。

## 3. 各種設定

・.envを作成
<pre>
$ cp env-example .env
</pre>

・.envにLINEチャネルキーを設定
<pre>
︙
"LINE_CHANNEL_SECRET" = xxxxx
"LINE_ACCESS_TOKEN" = xxxxx
</pre>

・APP_KEYを作成

<pre>
$php artisan key:generate
//base64:xxxxx が生成
</pre>

・ngrokで動作確認
<pre>
$ ngrok http xxxxx
//デフォルトは8080
</pre>

## 4a. Herokuにデプロイする場合

・Herokuのアカウントを作成し、アプリを新規作成

[![Deploy](https://www.herokucdn.com/deploy/button.png)](https://heroku.com/deploy)

・Herokuアプリへの環境変数の設定
<pre>
LINE_CHANNEL_SECRET - xxxxx
LINE_ACCESS_TOKEN - xxxxx

//SettingsからReveal Config Varsボタン
</pre>

・Herokuの環境変数にAPP_KEYを設定
<pre>
$ heroku config:set APP_KEY=base64: xxxxx -a herokuアプリケーション名
</pre>

## 4b. AWSにデプロイする場合
・EBにデプロイ
・Route53でドメインを取得
・Certificate Managerで証明書を発行
・ロードバランサーで設定
(参考URL)

## 5. LINE Console上でWebhookを設定
<pre>
https://xxxxx.herokuapp.com/api/meetups
//Heroku

https://xxxxx/api/meetups
//AWS
</pre>

## ・QRコード
![B909E27D-4072-4F2B-BF49-095F0473CD55](https://user-images.githubusercontent.com/60056670/76936499-64e37480-6936-11ea-9834-92e657e7ca42.jpeg)

LINEアプリで直接[URL](http://line.me/ti/p/@815sztgc)を開く。
>    – Tools –
>・PHP 7.3.14
>・Laravel 6.16.0
>・Docker 19.03.7
>・Git 2.21
>・AWS Elastic Beanstalk
>・Route53
>・Certificate Manager
>・LINE Messaging API (Flex Message)
>・Connpass API
>・ngrok

## ・ライセンス

The Laravel framework is open-source software licensed under the [MIT license](https://opensource.org/licenses/MIT).
