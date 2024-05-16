---
typora-copy-images-to: img
---
###  目录

[TOC]


### testForGit
0. git config --global user.name "username" 设置账户名和邮箱

​		git config --global user.email "email"

1. 在本地使用git init初始化当前目录为一个仓库

2. git add [文件名或目录]       跟踪文件或目录

   git rm [file]   取消文件的跟踪

   ```
   只对某种类型的文件进行跟踪，如md文档
   git add *.md  
   ```

3. git commit 提交暂存文件到本地仓库

   ```
   更快捷的命令
   git commit -am '提交信息'  
   ```

   <img src="img\QQ截图20230815170955.png" alt="QQ截图20230815170955" style="zoom:40%;" />

4. git status 查看当前文件提交状态

5. 远程仓库

   连接本地仓库到远程仓库

   ```shell
   git remote add origin https:/a;sldkgjlkjglkwejglkwe/xxx.git
   ```

   查看远程仓库

   ```shell
   git remote -v
   ```

   修改连接的远程仓库地址

   ```shell
   git remote set-url origin https:/a;sldkgjlkjglkwejglkwe/xxx.git 
   ```

6. 推送分支到远程仓库

7. 拉取冲突 [解决提交时文件不同步的问题](https://blog.csdn.net/m0_52316372/article/details/127446080?ops_request_misc=&request_id=&biz_id=102&utm_term=%20failed%20to%20push%20some%20refs%20to%20%27&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-127446080.142^v92^control&spm=1018.2226.3001.4187)  

   保存所有未提交的修改

   ```
   git stash
   git stash save "描述信息"    提交时可以添加描述信息
   ```

   查看和应用暂存

   ```
   git stash list
   git stash pop    会直接将最新的stash应用到工作目录中
   git stash drop 0 清楚最新的一个stash
   ```

   ​	`git pull -–rebase origin master` 操作，意为先取消commit记录，并且把它们临时保存为补丁(patch)(这些补丁在”.git/rebase”目录中)，之后同步远程库到本地，最后合并补丁到本地库之中

8. 提交到远程仓库

   ```
   git push origin master
   使用下面命令之后，每次提交代码时使用git push即可
   git push -u origin master
   ```

9. 显示提交历史

   ```
   git log
   git log --oneline  以一行简化的信息显示提交日志
   git log --all --graph  以图形化式显示各分支及merge历史
   查看最近3条更新日志，并且简单显示出所涉及的文件
   git log -3 --stat
   查看某一次提交的内容，执行下面命令（可以不加--stat）
   git show {commit_id} --stat
   ```

10. git diff 显示并编辑冲突的内容。 手动编辑冲突的文件，解决冲突。

​      在文件中，Git会用<<<<<<<、=======和>>>>>>>标记出冲突的部分。需要仔细检查这些标记之间的内容，并根据需要进行修改

```bash
查看该次提交与上次提交对所有文件所做的修改
git diff [commit_id]^
如下方式可以查看指定文件的修改
git diff commit_id -- <file_path>
```





### 分支

git brance feature 创建名为feature的分支

git branch --list 查看分支

```
git checkout feature1 切换到feature1分支上
git checkout <commit-hash> 切换到历史提交版本
git switch -         恢复到当前版本
```


### 合并

在切换到master分支之后使用 <u>git merge feature2</u>  将master2分支合并到主分支上。**如果有冲突conflict** 则使用vi编辑该文件修改文件为想要的那个改动再出来提交即可。



### 撤销提交reset

git reset head~ --soft   撤销最后一次commit（而之前使用git add设置的文件暂存状态仍然存在）

git reset head~             撤销commit以及暂存状态，但是修改过的内容还在

git reset head~ --hard 不光把暂存取消了，也把之前修改过的内容也撤销了  **慎用** 



### 基于ssh密钥身份验证

[Ubuntu中如何为 GitHub 设置基于 SSH 密钥的身份验证 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/377361811#:~:text=进入本地库目录并执行下一个命令以允许通过 SSH 工作： git remote set-url origin,git%40github.com%3Ausername%2Frepository-name.git 2. 直接通过 SSH 方式克隆库： git clone git%40github.com%3Ausername%2Frepository-name.git) 

```
ssh-keygen -t rsa -b 4096  生成一个新密钥对（一路回车即可）
cat ~/.ssh/id_rsa.pub   获取公钥文件内容
```

在github个人设置里面找到，点击后找到new ssh key

![image-20240315173453142](img\image-20240315173453142.png)

添加新身份并把获取的公钥文件内容复制进去即可

windows下使用同样指令，可以在用户目录下的隐藏文件中找到公钥文件id_rsa.pub

### 注意

1.在一个目录下执行git clone 命令，就可以把整个仓库拉取下来，这时候克隆下来的仓库会自动添加一个origin远程仓库指向github上的仓库。如果新建一个仓库，然后再链接远程仓库，也是一样的道理

