---
layout: post
category: Docker
tags: [Docker, Jenkins ]
description: DockerOnMacにjenkinsをインストールする手順
revdate:  2019-04-21  05:43 +0900
---
# Jenkins環境をDocker上に構築





## 環境

* MacOS Mojave (version 10.14.4)
* Docker version 18.09.2, build 6247962
* docker-compose version 1.23.2, build 1110ad01


## docker コンテナ の起動

`docker run` コマンドでdockerを起動します。

docker run -p 8080:8080   -v /srv/jenkins_home:/var/jenkins_home jenkins/jenkins:lts


```
mkdir -p /srv/jenkins_home
docker run -p 8080:8080 -p 50000:50000  -v /srv/jenkins_home:/var/jenkins_home jenkins/jenkins:lts
(略)
*************************************************************

Jenkins initial setup is required. An admin user has been created and a password generated.
Please use the following password to proceed to installation:

XXXXX

This may also be found at: /var/jenkins_home/secrets/initialAdminPassword

*************************************************************
*************************************************************
```


XXXXX のところにInitial Admin Password が表示されるのでコピーしておきます。
コピーを忘れても、/var/jenkins_home/secrets/initialAdminPasswordに書いてあるので、そのファイルを見れば問題ありません。

## docker compose で起動

[source,yml]
.docker-compose.yml
```
version: "3"
services:
  master:
    container_name: master
    image: jenkins:latest
    ports:
      - 8080:8080
    volumes:
      - ./jenkins_home:/var/jenkins_home

```

```
docker-compose up
Creating network "jenkins_default" with the default driver
Creating master ... done
...
```


## jenkins の初期設定

1. ブラウザで http://localhost:8080/ を開くと、Initial Admin Passwordを聞かれるので、先ほどのInitial Admin Passwordを入力します。
2. プラグインのインストールについて聞かれるので、「Install suggesed plugins」を選択します。
3. プラグインのインストールが完了したら、管理者アカウントを作成します。

あとは、通常のJenkinsの画面が表示されます。

[Jenkinsの管理]>[グローバルセキュリティの設定]へ移動します。
セキュリティを有効化のオプションを以下のように変更し、保存をクリックします。

* Jenkinsのユーザーデータベース　チェック
** ユーザーにサインアップを許可 チェックオフ
* 行列による権限設定 チェック
** 作成したユーザ名を入力して追加をクリック
** ユーザ名の行のチェックを全てオン


### ログインできなくなった場合の対処

/var/lib/jenkins/config.xmlを編集します。


 
./var/lib/jenkins/config.xml
```xml
<useSecurity>false</useSecurity>
```

その後Jenkisを再起動。
