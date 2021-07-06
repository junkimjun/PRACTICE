<https://docs.docker.jp/compose/environment-variables.html#substitute-environment-variables-in-compose-files>

COMPOSEにおける環境変数
----------------------

<br>

>composeの複数の場面において環境変数が様々に用いられている。
>これからそれに関する説明を行う。

<br>

Composerファイル内での環境変数の利用
----------------------------------

<br>

>　シェル内にて環境変数を設定し、その値をCOMPOSEファイル
>　において読み込ませることができる
>　web:
> image:"webapp:${TAG}" *${}--> 変数名

CONTAINER内での環境変数の設定
----------------------------

<br>

>　サービスコンテナにおいて、例えば、docker run-e VARIABLE=VALUE ....
>　のように　environment key使って、
>　環境変数を設定することが可能
>　web:
>>　environment:
>>>　-DEBUG=1

コンテナへの環境変数の受け渡し
----------------------------
シェル内の環境編素をenvironment keyを使って、直接サービスコンテナに
受け渡しことができる。　
EX）docker run -e 変数名。。。

>web:
 >environment:
    >-DEBUG  
    
コンテナ内のDEBUG変数は、シェル内のDEBUG変数の値が用いられる。

設定オプションー＞env_file
-------------------------
>外部ファイルから複数の環境変数をサービスコンテナー
>に受け渡しにはENV＿FILEオプションを利用することができる
>docker run --env-file=FILE...
>Web:
> env_file:
>    -web-varialbles.env

Docker-compose run実行時の環境変数の設定
---------------------------------------

<br>

>docker run -eと同じように、docker-compose run -eの実行に
>よるコンテナに対しても環境変数を設定することができる。
>docker-compose run -e DEBUG=1 web python console.py
>シェル変数を受け渡し際には、値は直接受け渡さず以下のようにできる
>docker-compose run -e DEBUG web python console.py
>コンテナ内のDEBUG変数は、シェル内のDEBUG変数の値が用いられる。
>このシェルとはComposeが起動しているシェルのこと

<br>

.envファイル
-----------

<br>

>Composeファイルが参照する環境変数、あるいはComposeの設定に用いられる
>環境変数のデフォルト値を設定することができる。
>これは.envという環境ファイルにて行う。
>$ cat .env
>TAG=v1.5
>$ cat docker-compose.yml
>version: '3'
>services:
>   web:
>     image: "webapp:${TAG}
> 　docker-compose upを実行すると、上で定義されているWEBサービスは
> 　WEBAPP:v1.5というイメージを利用する。このことはCONFIGコマンドを
> 　使って確認できる。このコマンドは変数を返還した後のアプリケーション
> 　設定を端末画面に出力します。

<b>

>　$docker-compose config
>　version: '3'
 >　services:
    >　web:
       >　image: 'webapp:v1.5'
>　シェル内にて設定される値は、.envファイル内のものよりも
　>優先されます。例えばシェル上においてTAGを異なる値に設定していたら、
>　それを使って変数返還されたIMAGEが用いられることになります。
>　$export TAG=v2.0
>　$docker-compose config
>　version: '3'
>　services:
  >　web:
    >　image: 'webapp:v2.0'
>　environmentとenv_fileによる設定ファイルの両方にて変数がしてされると
>　環境変数の値はまずはenvironmentキーが優先して取得され、次に
>　設定ファイルから取得することにより、
>　その次にDOCKERFILEのENVエントリとなります。
  


