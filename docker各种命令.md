# docker命令

### 基本命令

```
查询docker版本信息
docker --version
查看docker服务状态
sudo systemctl status docker
```

```
列出已安装的docker镜像
docker images
```

```
启动一个容器
docker start <id_dawl;kgroi90>
停止一个容器
docker stop <id_2383d9f8a>
```

```
列出正在运行的容器
docker ps 
列出所有的容器（包括已停止）
docker ps -a
```

```
根据ID进入对应的容器/环境
docker exec -it 8c9475f992bb /bin/bash
```



### 链接

[Docker 1小时快速上手教程，无废话纯干货_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV11L411g7U1/?spm_id_from=333.788.recommend_more_video.-1&vd_source=b48e4671f9c3de637ed43d333edd10c7) 