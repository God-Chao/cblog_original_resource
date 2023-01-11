---
title: docker常用指令
category: 笔记
tags:
  - docker
  - 指令
banner_img: /img/banner/docker.jpg
index_img: /img/cover/docker.jpg
excerpt: docker基础指令以及集成各种第三方服务配置
date: 2022-11-22 16:12:48
---
## 1.安装Docker

**使用国内 daocloud 一键安装命令**

```bash
$ curl -sSL https://get.daocloud.io/docker | sh
```

**开启docker服务**

```bash
$ systemctl start docker
```

**配置国内镜像源**

```bash
$ vim /etc/docker/daemon.json
```

**将以下内容复制进去**

```json
{
  "registry-mirrors": ["https://abhm2hdj.mirror.aliyuncs.com"]
}
```

**重启docker**

```bash
$ systemctl restart docker
```

**查看docker版本**

```bash
$ docker -v
```

## 2.镜像命令

**查看本地镜像**

```bash
$ docker images
```

**搜索镜像**

```bash
$ docker search 镜像名
```

**拉取镜像**

```bash
$ docker pull 镜像名:版本号
```

**查看本地镜像id**

```bash
$ docker images -q
```

**删除镜像**

```bash
$ docker rmi 镜像名
```

## 3.容器命令

**查看容器**

```bash
#查看正在运行的容器
$ docker ps
#查看所有容器
$ docker ps -a  
```

**创建并启动容器**

```bash
# -i 保持容器运行，退出容器后自动关闭
# -t 为容器重新分配一个伪输入终端
# -d 后台运行容器，需要使用docker exec进入容器
# -it 交互式容器
# -id 守护式容器
--name 为创建的容器命名
$ docker run 参数
```

**进入容器**

```bash
$ docker exec 参数
```

**创建一个后台运行的容器**

```bash
$ docker run -id --name 容器名称 镜像名称:版本号
```

**容器的启动与删除**

```bash
$ docker start 容器名称
$ docker stop 容器名称
$ docker restart 容器名称
$ docker rm 容器名称
```

**查看容器信息**

```bash
$ docker inspect 容器名称
```

**设置容器自启动**

```bash
$ docker update 容器名称 --restart=always
```

## 4.Docker安装mysql

**拉取mysql最新镜像**

```bash
$ docker pull mysql:latest
```

**查看镜像是否下载成功**

```bash
$ docker images
```

**创建并运行mysql容器**

```bash
# docker run : 创建并运行一个容器
# –-name : 给容器起一个名字, 比如叫做 mysql
# -p : 将宿主机端口与容器端口映射, 冒号左侧是宿主机端口, 右侧是docker容器端口
# mysql : 镜像名称
$ docker run -itd --name mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=root mysql
```

**检查容器是否启动成功**

```bash
$ docker ps -a
```

**进入mysql容器**

```bash
$ docker exec -it mysql bash
```

**登录mysql**

```bash
> mysql -u root -p
# 输入quit退出mysql命令行，返回容器命令行
# 输入exit退出容器命令行，回到linux命令行
```

## 5.Docker安装redis

**拉取redis最新镜像**

```bash
$ docker pull redis:latest
```

**查看镜像是否下载成功**

```bash
$ docker images
```

**创建并运行redis容器**

```bash
# docker run : 创建并运行一个容器
# –-name : 给容器起一个名字, 比如叫做 redis
# -p : 将宿主机端口与容器端口映射, 冒号左侧是宿主机端口, 右侧是docker容器端口
# redis : 镜像名称
$ docker run -itd --name redis -p 6379:6379 redis
```

**检查容器是否启动成功**

```bash
$ docker ps -a
```

**进入redis容器**

```bash
$ docker exec -it redis bash
```

**打开redis客户端**

```bash
> redis-cli
# 输入quit退出redis命令行，返回容器命令行
# 输入exit退出容器命令行，回到linux命令行
```

## 6.Docker安装RabbitMQ

**拉取rabbitmq最新镜像**

```bash
$ docker pull rabbitmq:latest
```

**查看镜像是否下载成功**

```bash
$ docker images
```

**创建并运行rabbitmq容器**

```bash
# docker run : 创建并运行一个容器
# –-name : 给容器起一个名字, 比如叫做 rabbitmq
# 第一个-p ：用于页面访问使用
# 第二个-p ：用于生产和消费端使用（也就是再代码里使用）
# rabbitmq : 镜像名称
# d：后台运行
$ docker run --name rabbitmq -p 15672:15672 -p 5672:5672 -d rabbitmq
```

**检查容器是否启动成功**

```bash
$ docker ps -a
```

**进入rabbitmq容器**

```bash
$ docker exec -it rabbitmq bash
```

**下载图形插件**

```bash
rabbitmq-plugins enable rabbitmq_management
```

**访问：ip:15672**

## 7.Docker部署jar包

**将jar包传输到/Downloads/docker-files目录下（以test.jar为例）**

**在该目录下创建并编辑Dockerfile文件**

```bash
$ vim Dockerfile
```

**输入以下内容：**

```plaintext
FROM java:8  # 指定jdk版本，会自动在docker中pull对应的镜像
MAINTAINER Chao <chao-j@qq.com>  # 指定作者和邮箱
ADD cblog.jar cblog.jar  # 将该jar包添加到docker镜像中，左边为源文件名，右边为镜像名
ENTRYPOINT ["java","-jar","cblog.jar"]  # jar的运行命令
```

**打包镜像**

```bash
$ docker build -t cblog .
```

**查看镜像是否正常创建**

```bash
$ docker images
```

**创建并运行容器**

```bash
# 这里左边的端口为外部访问的端口，右边为容器内容端口（因为tomcat默认为8080，所以此处最好不改）
$ docker run -it -d --name cblog -p 8081:8080 cblog
```

**调用接口测试是否部署成功**

**查看日志**

```bash
$ docker logs test
```

## 8.Docker安装nginx

**拉取nginx最新镜像**

```bash
$ docker pull nginx:latest
```

**查看镜像是否下载成功**

```bash
$ docker images
```

**创建好目录**

```plaintext
nginx
- conf
	- nginx.conf
- html
	- index.html
- logs
```

**将以下内容复制进nginx.conf（官方配置，可先运行一个nginx容器，在容器/etc/nginx/nginx.conf中可找到）**

```plaintext
user  nginx;
worker_processes  auto;

error_log  /var/log/nginx/error.log notice;
pid        /var/run/nginx.pid;


events {
    worker_connections  1024;
}


http {
    include       /etc/nginx/mime.types;
    default_type  application/octet-stream;

    log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
                      '$status $body_bytes_sent "$http_referer" '
                      '"$http_user_agent" "$http_x_forwarded_for"';

    access_log  /var/log/nginx/access.log  main;

    sendfile        on;
    #tcp_nopush     on;

    keepalive_timeout  65;

    #gzip  on;

    include /etc/nginx/conf.d/*.conf;
}
```

**在nginx目录下运行容器（挂载对应的目录和文件）**

```bash
$ docker run --name nginx -p 80:80 -d \
-v $PWD/conf/nginx.conf:/etc/nginx/nginx.conf \
-v $PWD/logs:/var/log/nginx \
-v $PWD/html:/usr/share/nginx/html \
nginx
```

**访问ip地址查看是否启动成功**

## 9.Docker安装mongoDB

**拉取mongoDB最新镜像**

```bash
$ docker pull mongo:latest
```

**查看镜像是否下载成功**

```bash
$ docker images
```

**创建并运行mongoDB容器**

```bash
# --auth : 需要密码才能访问容器服务
$ docker run -itd --name mongo -p 27017:27017 mongo --auth
```

**检查容器是否启动成功**

```bash
$ docker ps -a
```

**以管理员身份进入容器内部**

```bash
$ docker exec -it mongo mongo admin
```

**创建用户，切记只有这样创建用户才拥有所有权限！！！**

```bash
> db.createUser({user: 'chao',pwd: 'chao',roles: [ { role: 'root', db: 'admin' } ]});
```

**尝试使用上面创建的用户信息进行连接**

```bash
> db.auth('chao', 'chao')
```

**使用图形工具连接url：mongodb://用户名:密码@ip地址:27017**

## 10.数据卷挂载

**查看所有数据卷**

```bash
$ docker volume ls
```

**创建数据卷**

```bash
$ docker volume create 数据卷名称
```

**删除数据卷**

```bash
$ docker volume rm 数据卷名称
```

**清除没用的数据卷**

```bash
$ docker volume prune
```

**查看指定数据卷信息**

```bash
$ docker volume inspect 数据卷名称
```

**docker挂载**

```bash
$ docker run -d -P \
--name web \
--mount type=bind,source=/src/webapp,target=/usr/share/nginx/html \
nginx:alpine
```
