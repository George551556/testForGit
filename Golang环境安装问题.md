---
typora-copy-images-to: img
---

## Ubuntu安装go环境

- 查看系统架构是arm架构还是AMD架构，再从官网下载对应正确的安装包

  ```
  lscpu | grep Architecture
  ```

  ![image-20240315170440804](img\image-20240315170440804.png)


- 设置国内下载代理源

  ```
  go env -w GOPROXY=https://goproxy.cn,direct 
  go env GOPROXY #查看当前
  
  恢复为原来默认的下载源
  go env -w GOPROXY=https://proxy.golang.org
  ```

- 用安装包安装环境

  ```
  1.解压到对应位置
  sudo tar -C /usr/local -xzf go1.15.linux-amd64.tar.gz
  2.打开文件
  vi ~/.bashrc
  	2.1粘贴该行到文件末尾
  	export PATH=$PATH:/usr/local/go/bin  # 把编译器主目录加入环境变量
  	2.2粘贴下面这行，即把工作区目录GOPATH加入环境变量（使用go install编译后的可执行文件都会放在该目录下，使用对应指令即可直接运行）
  	export PATH=$PATH:/home/karen/go/bin # 需要把“karen”替换为实际用户名
  
  3.使 
  source ~/.bashrc
  ```
  
  

## 卸载go环境

对于手动安装

```
# 删除go目录(使用go env查看GOROOT的目录)
go env|grep GOROOT
sudo rm -rf /usr/local/go
# 删除删除软链接
sudo rm -rf /usr/bin/go
```

对于自动安装

```
sudo apt-get remove golang-go
sudo apt-get remove --auto-remove golang-go
```

