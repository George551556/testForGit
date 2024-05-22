# docker命令

### 基本命令

```
启动docker
systemctl start docker
systemctl stop docker
```

```
查询docker版本信息
docker --version
查看docker服务状态
sudo systemctl status docker
```

```
查询官方容器库
docker search [name]  #docker search mysql
拉取/下载镜像
docker pull [name]
列出已安装的docker镜像
docker images
```

```
从镜像启动一个容器，同时进入容器，此时退出的话容器也会直接关闭
docker run -it [镜像名]
在后台启动并长期保持一个容器
docker run -d -it [镜像名]
端口：[宿主机端口：容器内部端口]
docker run -d -it --name my_container -p 8080:80 -v /data:/var/www my_image
启动一个（已有）容器
docker start <id_dawl;kgroi90>
停止一个（已有）容器
docker stop <id_2383d9f8a>
```

```
列出正在运行的容器
docker ps 
列出所有的容器（包括已停止）
docker ps -a
停止容器
docker stop 容器ID
删除容器
docker rm 容器ID
删除镜像（执行这个之前必须先停止并删除基于此镜像的所有容器）
docker rmi 该镜像ID
```

```
根据ID进入已打开的容器/环境
docker exec -it 8c9475f992bb /bin/bash
```

```
从宿主机向容器传递文件或目录
docker cp local_file.txt container_ID:/path/to/container/
或者反向传文件，则互换源和目的路径
```

```
重启docker服务
sudo systemctl daemon-reload 和 sudo systemctl restart docker
```



### 链接

[Docker 1小时快速上手教程，无废话纯干货_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV11L411g7U1/?spm_id_from=333.788.recommend_more_video.-1&vd_source=b48e4671f9c3de637ed43d333edd10c7) 

[Ubuntu安装docker教程](https://zhuanlan.zhihu.com/p/651148141)