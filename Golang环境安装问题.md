---
typora-copy-images-to: img
---

## Ubuntu安装go环境

- 查看系统架构是arm架构还是AMD架构，再从官网下载对应正确的安装包

  ```
  lscpu | grep Architecture
  ```

  ![image-20240315170440804](C:\Users\JackLiu\Pictures\typora\image-20240315170440804.png)


- 设置国内下载代理源

  ```
  go env -w GOPROXY=https://goproxy.cn,direct 
  go env GOPROXY #查看当前
  ```

- 用安装包安装环境

  ```
  解压到对应位置
  sudo tar -C /usr/local -xzf go1.15.linux-amd64.tar.gz
  打开文件
  vi ~/.bashrc
  粘贴该行到文件末尾
  export PATH=$PATH:/usr/local/go/bin
  
  source ~/.bashrc
  ```
  
  

## 卸载go环境

对于手动安装

```
# 删除go目录(使用go env查看GOROOT的目录)
sudo rm -rf /usr/local/go
# 删除删除软链接
sudo rm -rf /usr/bin/go
```

对于自动安装

```
sudo apt-get remove golang-go
sudo apt-get remove --auto-remove golang-go
```

