centos7中安装完毕后,没有进行ssh配置,很多默认选项会导致ssh链接过慢,以下修改可以秒连接服务器ssh.

1、关闭DNS反向解析

```
# vi /etc/ssh/sshd_config
UseDNS=no
把文件中#UseDNS=yes改为UseDNS=no,因为虽然代码是注释状态,但是默认他是yes开启
```

2、关闭SERVER上的GSS认证

```
# vi /etc/ssh/sshd_config
GSSAPIAuthentication no
在文件中搜索以上GSSAPIAuthentication文字,把yes改为no,如代码最前有注释符号#,记得把注释符去掉
```

3、重启sshd服务

```
systemctl restart sshd
```

4、ssh链接以后默认3分钟内无操作,会断开链接.改进一下

```
打开/etc/ssh/sshd_config 找到以下代码
#ClientAliveInterval 60
#ClientAliveCountMax 3
改为
ClientAliveInterval 60
ClientAliveCountMax 3
保存后重启ssh
systemctl restart sshd
```

搞定,秒连接服务器ssh.