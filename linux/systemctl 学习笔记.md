## **systemctl 学习笔记**



systemctl命令 是系统服务管理器指令，它实际上将 service 和 chkconfig 这两个命令组合到一起。

| 任务                 | 旧指令                        | 新指令                                                       |
| -------------------- | ----------------------------- | ------------------------------------------------------------ |
| 使某服务自动启动     | chkconfig --level 3 httpd on  | systemctl enable httpd.service                               |
| 使某服务不自动启动   | chkconfig --level 3 httpd off | systemctl disable httpd.service                              |
| 检查服务状态         | service httpd status          | systemctl status httpd.service （服务详细信息） systemctl is-active httpd.service （仅显示是否 Active) |
| 显示所有已启动的服务 | chkconfig --list              | systemctl list-units --type=service                          |
| 启动某服务           | service httpd start           | systemctl start httpd.service                                |
| 停止某服务           | service httpd stop            | systemctl stop httpd.service                                 |
| 重启某服务           | service httpd restart         | systemctl restart httpd.service                              |



### 实例

`systemctl start httpd.service` # 启动服务

`systemctl enable httpd.service` # 设置开机自启动

`systemctl disable httpd.service` # 停止开机自启动

`systemctl status httpd.service` # 查看服务当前状态

`systemctl restart httpd.service` # 重新启动某服务

`systemctl list-units --type=service` # 查看所有已启动的服务



系统服务目录：/usr/lib/systemd/system/ 

用户服务目录：/usr/lib/systemd/user/

在/usr/lib/systemd/system目录下新建service-name.service文件（需要可执行权限）

```
[UNIT]

#服务描述

Description=Server Description

#指定了在systemd在执行完那些target之后再启动该服务

After=network.target



[Service]

#定义Service的运行类型，一般是forking(后台运行)   

Type=forking

#定义PID文件的路径

PIDFile=



#定义systemctl start|stop|reload *.service 的执行方法（具体命令需要写绝对路径）

#注：ExecStartPre为启动前执行的命令

ExecStartPre=

ExecStart=

ExecReload=

ExecStop=



#创建私有的内存临时空间

PrivateTmp=True



[Install]

#多用户

WantedBy=multi-user.target
```





### 配置权限

`chmod -R 754 /lib/systemd/system`

### 重载系统服务

`systemctl daemon-reload`



### 参考：

https://blog.csdn.net/qq_25821067/article/details/79120222

http://www.ruanyifeng.com/blog/2016/03/systemd-tutorial-commands.html

http://www.ruanyifeng.com/blog/2016/03/systemd-tutorial-part-two.html



### \# 查看指定服务日志 -f 实时

`journalctl -u google.service -f`



### \# 查看日志占用空间大小

`journalctl --disk-usage`



### \# 指定保留日志文件大小

`journalctl --vacuum-size=1G`



### \# 删除日志文件

`rm -rf /var/log/journal/*`