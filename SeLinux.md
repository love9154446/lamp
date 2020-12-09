关闭seliux

首先要临时关闭,否则设置目录权限无效.

```
setenforce 0
```

打开文件/etc/selinux/config

```
SELINUX=enforcing修改为SELINUX=disabled
```

设置目录写入权限777

```
chmod -R 777 127
```

关闭防护墙,关闭开机启动

```
systemctl stop firewalld.service
systemctl disable firewalld.service
```

修改httpd.conf

```
找到LoadModule headers_module /usr/lib64/httpd/modules/mod_headers.so
如果该行有注释符号#,需要去掉,否则会显示默认页面.
```

