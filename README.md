---
typora-copy-images-to: img
---
# testForGit
该仓库是为了学习git提交的相关操作

1.在本地使用git init初始化当前目录为一个仓库

2.git add [文件名或目录]       跟踪文件或目录

3.git commit 提交暂存文件到本地仓库

<img src="img\QQ截图20230815170955.png" alt="QQ截图20230815170955" style="zoom:40%;" />

4.git status 查看当前文件提交状态

5.git remote add origin https:/a;sldkgjlkjglkwejglkwe/xxx.git     连接本地仓库到一个**远程仓库**

​	git remote set-url origin https:/a;sldkgjlkjglkwejglkwe/xxx.git   修改连接的远程仓库地址

6.git push origin master   推送分支到远程仓库

​		若是第一次提交给远程仓库 可以使用 **git push -u origin master**   之后每次使用 **git push** 即可提交远程仓库。非常方便。

7.[解决一个提交时文件不同步的问题](https://blog.csdn.net/m0_52316372/article/details/127446080?ops_request_misc=&request_id=&biz_id=102&utm_term=%20failed%20to%20push%20some%20refs%20to%20%27&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-127446080.142^v92^control&spm=1018.2226.3001.4187)  

​	`git pull -–rebase origin master` 操作，意为先取消commit记录，并且把它们临时保存为补丁(patch)(这些补丁在”.git/rebase”目录中)，之后同步远程库到本地，最后合并补丁到本地库之中

8.git commit -am '提交信息'   可以直接默契修改过的文件并提交

9.git log 显示提交历史

10.git log --all --graph  以图形化式显示各分支及merge历史

### 分支

git brance feature 创建名为feature的分支

git branch --list 查看分支

git checkout feature1 切换到feature1分支上



### 合并

在切换到master分支之后使用 <u>git merge feature2</u>  将master2分支合并到主分支上。**如果有冲突conflict** 则使用vi编辑该文件修改文件为想要的那个改动再出来提交即可。



### 撤销提交reset

git reset head~ --soft   撤销最后一次commit（而之前使用git add设置的文件暂存状态仍然存在）

git reset head~             撤销commit以及暂存状态，但是修改过的内容还在

git reset head~ --hard 不光把暂存取消了，也把之前修改过的内容也撤销了  **慎用** 





### 注意

1.在一个目录下执行git clone 命令，就可以把整个仓库拉取下来，这时候克隆下来的仓库会自动添加一个origin远程仓库指向github上的仓库。如果新建一个仓库，然后再链接远程仓库，也是一样的道理

2.**我王少斌是烧杯** 

<img src="img\222.png" alt="QQ截图20230815170955" style="zoom:40%;" />
