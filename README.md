# testForGit
该仓库是为了学习git提交的相关操作

1.在本地使用git init初始化当前目录为一个仓库

2.git add [文件名或目录]       跟踪文件或目录

3.git commit 提交暂存文件到本地仓库

4.git status 查看当前文件提交状态

5.git remote add origin https:/a;sldkgjlkjglkwejglkwe/xxx.git     连接本地仓库到一个远程仓库

6.git push origin master   推送分支到远程仓库

7.[解决一个提交时文件不同步的问题](https://blog.csdn.net/m0_52316372/article/details/127446080?ops_request_misc=&request_id=&biz_id=102&utm_term=%20failed%20to%20push%20some%20refs%20to%20%27&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-1-127446080.142^v92^control&spm=1018.2226.3001.4187)  

​	`git pull -–rebase origin master` 操作，意为先取消commit记录，并且把它们临时保存为补丁(patch)(这些补丁在”.git/rebase”目录中)，之后同步远程库到本地，最后合并补丁到本地库之中

8.还没
