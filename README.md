**注)各コンテナイメージを利用前に必ずライセンス条項を確認する**

# Docker でコンテナを起動する(Docker for Windows)
## nginx
```
docker run -d -p 8080:80 nginx
```

## Tomcat
```
docker run -d -p 8081:8080 tomcat:8.0
docker run -it --rm -p 8081:8080 tomcat:8.0
```

## Oracle
※Oracle のライセンス条項を確認する
https://hub.docker.com/_/oracle-database-enterprise-edition

```
docker run -d -it --name myoracle store/oracle/database-enterprise:12.2.0.1
docker exec -it myoracle bash
sqlplus sys/Oradoc_db1@ORCLCDB as sysdba
```

## Python
```
docker run -it --rm python:3.7.2-alpine3.8 sh
docker run -it --rm python:3.7.2-alpine3.8 python
```

# Docker でコンテナを起動する(Azure Container Instance)
```
az group create --name myResourceGroup --location eastus 
az container create --resource-group myResourceGroup --name mycontainer --image microsoft/aci-helloworld --dns-name-label aci-demo --ports 80
```

# コンテナをカスタマイズする
## 方法1 : コンテナにログインしてファイルの変更を行う
```
docker exec -it ID bash
cd /usr/share/nginx/html/
echo "Hello world" > index.html
```

## 方法2 : Dockerfile でコンテナを作ってみる
### 1. nginx のカスタム
```
cd nginxcustom
docker build -t tsubasaxzzz/nginx1231 .
docker run -d -p 8080:80 tsubasaxzzz/nginx1231
```

### 2. ASP.net
作成
```
cd ASP.NET-sample
docker build -t tsubasaxzzz/website2 .
```

起動
```
docker run -p 8000:80 -d tsubasaxzzz/website2
```

## 複数のコンテナを同時に起動させる(docker-compose)
### 作成
```
cd wordpress
docker-compose.exe up
```
### 削除
```
docker-compose.exe rm -f
docker volume ls
docker volume rm wordpress_db_data
```
