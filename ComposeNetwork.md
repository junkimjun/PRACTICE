<https://docs.docker.jp/compose/networking.html>

Composeのネットワーク機能
-----------------------

>デフォルトでComposeは、アプリ向けに単一の
>ネットワークを設定します。一つのサービスを
>構成する各コンテナは、そのデフォルトのネット
>ワークに参加するので、ネットワーク上の他の
>コンテナからのアクセスが可能です。さらに
>コンテナ名と同等のホスト名を用いてコンテナの
>識別が可能となります。
>例えばアプリがmyappというディレクトリにあって、docker-compose.ymlが以下のような
>内容であるとしましょう。

<br>

> version: "3"
> services:
>   web:
>     build:
>     ports:
>       -"8000:8000"
>   db:
>     image: postgres
>     ports: 
>       - "8001:5432"
> docker-compose upを実行すると以下の結果となる

>１、myapp
>version: '2'
>  web:
>   built:
>   ports:
>     - "8000:8000"
>   db:
>    image: postgres

> docker-compose up -> 
> 1.myapp_default という名称のネットワークを作成します。
> 2.WEB設定を使ったコンテナを作成します。これをネットワーク　
>   myapp_defaultに対して、ＷＥＢという名称で追加します。
> 3.DB設定を使ったコンテナを作成します。これをネットワークMYADPP_DEFAULTに
> 　対して、ＤＢという名称で作成します。
> 　各コンテナは、これでホスト名をWEBあるいはdbで名前解決することにより、
> 　コンテナに割り当てられたＩＰアドレスがわかります。例えば、ＷＥＢアプリケーション
> 　のコードがＵＲＬ　postgres://my
> 　
