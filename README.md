1，确保已经开启权限，第一步需要做的就是开启可以运行自己应用的权限。

Additional services -> Run your own applications -> Enabled 如果不开启这一项，自己的用户目录下的所有文件都无法添加可执行权限。

2，配置端口号

按顺序打开添加端口号Port reservation->Add port->Random->add

3，ssh 进入 服务器

s6.serv00.com可能会因为被墙连不上,可以用web6.serv00.com或者cache6.serv00.com

ssh -p 22 <Login>@<SSH/SFTP服务器地址>  如果不会使用终端可采用其他ssh工具或者webssh，只需要输入账号密码端口即可

4，拉取代码到指定目录

cd ~/domains && git clone https://github.com/DemonFengYuXiang/serv00-script.git && cd serv00-script && bash vless.sh

5，执行命令

cd ~/domains/$USER.serv00.net/vless && ./check_vless.sh -p <端口号>

6，复制信息中返回的vless信息并粘贴到 v2ray中使用

7，配置定时任务维护节点

在面板中依次打开Cron jobs->Add cron job->Specify time选择每小时执行一次Hourly->Command中输入以下命令

cd ~/domains/$USER.serv00.net/vless && ./check_vless.sh

六、其他常用命令
1，删除vless节点代码以及进程关闭

pm2 delete vless && rm -rf ~/domains/serv00-script && rm -rf ~/domains/$USER.serv00.net/vless

2，查看当前vless节点状态

pm2 status

# 如果状态异常可以执行以下命令重启

cd ~/domains/$USER.serv00.net/vless && ./check_vless.sh

3，查看错误日志
如果出现异常可以执行以下命令查看日志截图发到TG群聊解决

pm2 logs
后续其他命令修改待更新！！！
