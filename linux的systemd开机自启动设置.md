### 步骤

1. 在`/etc/systemd/system`目录下创建类似`mytask.service`的文件，文件内容格式如下：

   > 部署时需要删除所有注释，否则报错

   ```bash
   [Unit]
   Description=MyApp Service
   After=network.target     #可选，等待网络连接后再启动想要的程序
   After=mysql.service		#可选，等待数据库启动后再启动程序
   
   [Service]
   WorkingDirectory=/home/karen/project/getBilicount  #可选，设置程序的工作目录（某些运行需要同目录下其他的文件的程序需要），但我使用中有问题
   TimeoutStartSec=300   #可选，最多等待该设定的秒数后则认为程序启动失败，但我实际使用中似乎没用
   ExecStartPre=/bin/sleep 120  # 在启动服务之前等待 120 秒
   ExecStart=/home/karen/project/getBilicount/getBiliCnt #执行程序的主要参数，务必使用绝对路径！！
   StandardOutput=append:/home/karen/project/getBilicount/log.log #日志和报错可以重定向到指定目录，要求绝对路径，可根据情况保留
   StandardError=append:/home/karen/project/getBilicount/log.log
   Restart=always  #启动不成功时持续尝试启动程序，建议保留
   User=karen		#指定用户
   
   [Install]
   WantedBy=multi-user.target
   ```

2. 执行下面命令加载`systemd`守护进程，（后续只要修改service文件后都要执行该命令）

   ```bash
   sudo systemctl daemon-reload
   ```

3. 执行命令设置为开机自启动

   ```bash
   sudo systemctl enable mytask.service
   ```

4. 补充命令

   ```bash
   sudo systemctl start mytask.service  	# 手动启动该任务
   sudo systemctl restart mytask.service  	# 重新启动该任务
   sudo systemctl status mytask.service   	# 查看程序的当前状态
   sudo systemctl disable mytask.service	# 禁止服务自启动
   ```



### 注意

- 每个想要自启动的程序都要单独创建一个对应的*service*文件来启动