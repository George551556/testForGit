## 问题1

在linux上导出表的数据时权限1290报错

#### 原因

在对应目录没有操作权限

#### 解决方法

进入MySQL使用以下命令查看可保存文件的目录

```
select @@datadir;
```

输出结果：

![image-20231210131109500](img\image-20231210131109500.png)

再使用以下命令查看安全目录参数

```sql
show variables like '%secure%'
```



![image-20231210130421972](img\image-20231210130421972.png)

<a id="aiobj">设置</a>secure_file_priv的值与上面datadir的一样，使用如下命令打开并编辑

```
vi /etc/my.cnf #我是这种方式打开
vi /etc/mysql/my.cnf
```

在打开的文件中设置secure_file_priv的值（如果没有则自己添加，如下，在[mysqld]部分添加）

```
secure-file-priv = /path/to/your/directory
```

之后使用命令重启MySQL

```
sudo systemctl restart mysql
```

最后将需要保存的表数据直接放在该目录下即可

![image-20231210131333767](img\image-20231210131333767.png)



## 问题1-新

> 25.2.2日在阿里云服务器上的MySQL（使用宝塔安装）导出数据又权限不足，上面的解决方法无效，以下为新的解决方法：

---

- 先设置导出目录，类似[上面方法](#aiobj)，**建议导出目录**设置为`/var/lib/mysql-files`，同时在对应位置创建该目录，（这个目录是MySQL默认允许的安全导入导出目录，其他路径如/root通常不适合用于MySQL文件操作，而云服务器默认是使用root用户登录，因此可能是造成这个问题的原因）
- 使用root权限进入数据库执行...into outfile...导出数据，即可成功



## 问题2

在将txt数据导入到windows上的MySQL时报错，同样为权限问题

ERROR 2068 (HY000): LOAD DATA LOCAL INFILE file request rejected due to restrictions on access

#### 解决方法

1.使用如下命令进入数据库，在本地客户端启用加载本地数据功能

```
mysql -u username -p --local-infile=1
```

2.编辑 MySQL 的配置文件（通常是 `/etc/mysql/my.cnf` 或 `/etc/my.cnf`），在 `[mysqld]` 部分添加或修改以下行（windows下为my.ini）

```
[mysqld]
local-infile=1
```

使用命令导入（windows下需要切换分隔符为\\）

```
load data local infile 'C:\\Users\\JackLiu\\Desktop\\fsdownload\\todolist_save_users.txt' into table users;
```



## 导入导出命令

**导出为txt**

> 这里的“into outfile”是语法关键字，无需改变

```
select * from table_name into outfile '/www/server/data/test.txt';
```

导入（注意：若表中原本有数据，即便设置了值唯一的id也会强制添加数据项，会保持两个相同的id都存在）

```
load data local infile 'C:\\Users\\lkz\\Desktop\\dir_s\\test.txt' into table table_name;
```

**导出为sql**

1.执行下命令导出数据库结构和数据(之后需要输入密码即可)，导出地址无需加引号

```
mysqldump -u root -p db_name > C:\Users\lkz\Desk\test.sql
```

2.导入库和数据，在进入MySQL后执行如下命令。linux系统用绝对地址即可

```
source C:\Users\lkz\Desk\test.sql
```

如果是在docker容器中的MySQL

```
先将文件导入到容器
docker cp **.sql 容器名或ID:/root/
docker cp test.sql 32453245:/root/
进入容器再进入root目录
#docker exec -it 【容器名/ID】/bin/bash
将文件导入数据库
# mysql -u root -p da_name < test.sql
```





## 命令补充

#### docker命令详情

[本地文件](docker各种命令.md) 

#### linux

```
# 可在前面加个sudo
service mysql start
service mysql stop
....          restart

# 备份整个数据库
mysqldump -u root -p --all-databases > backup.sql
# 备份指定名称数据库
mysqldump -u root -p --databases mydatabase > backup.sql
```







