### linux 自启动

chkconfig sshd on

https://blog.csdn.net/yuxuan_08/article/details/72863720


### chkconfig 安装

apt-get install sysv-rc-conf
cp /usr/sbin/sysv-rc-conf /usr/sbin/chkconfig

https://blog.csdn.net/weixin_42930696/article/details/88964311

chkconfig 是 centOS下面的
ubuntu aliyun的源 无法安装 sysv-rc-conf，需要增加ubuntu的源


[TODO] 还有一个bug，chkconfig 显示都是系统自启动，重启之后还是没有效果