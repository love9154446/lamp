1.安装Mysql5.7

```
wget -i -c http://dev.mysql.com/get/mysql57-community-release-el7-10.noarch.rpm
yum -y install mysql57-community-release-el7-10.noarch.rpm
yum -y install mysql-community-server

systemctl start mysqld
systemctl enable mysqld
head -100 /var/log/mysqld.log              //查找localhost对应的密码uHBZgHa?V52z
mysql -uroot -p  //需要输入临时密码进入ALTER USER 'root'@'localhost' IDENTIFIED BY 'Hyf3961056@';
mysql> ALTER USER 'root'@'localhost' IDENTIFIED BY 'Hyf3961056@';
```

2.安装php7.2环境

```
首先获取rpm：
rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm

然后可以利用 sudo yum list php*查看目前都有php的什么版本了，我们这里安装7.2版本：
yum -y install php72w -y

但安装完毕后，输入php -v发现并没有该命令，因为php72w只是安装了php最小的库，一些应用还未安装，因此安装一些拓展包即可：
yum -y install php72w-cli php72w-common php72w-devel php72w-mysql php72w-gd.x86_64

对于wordpress应用，可能还需安装如下包：
sudo yum -y install php72w-gd php72w-imap php72w-ldap php72w-odbc php72w-pear php72w-xml php72w-xmlrpc

然后输入php -v出现如下信息：
[c@localhost ~]$ php -v
PHP 7.2.5 (cli) (built: Apr 28 2018 07:30:30) ( NTS )
Copyright (c) 1997-2018 The PHP Group
Zend Engine v3.2.0, Copyright (c) 1998-2018 Zend Technologies
```

3.安装apache2.4.6

```
yum install -y httpd httpd-devel
systemctl start httpd
systemctl enable httpd
配置HTTPS
yum install mod_ssl openssl
yum install openssl
```

