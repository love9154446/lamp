安装v2ray代理软件

前言:我们需要一台香港或者国外服务器,可以访问被墙的网址,进行以下配置.

1.输入下面命令安装

```
bash <(curl -s -L https://git.io/v2ray.sh)
```

如果提示 curl: command not found ，那是因为你的 VPS 没装 Curl

centos 系统安装 Curl 方法: 

```
yum update -y && yum install curl -y
```

2.链接代理服务器,使用v2rayN

```
添加服务器类型选择(vmess服务器);
在加密方式里面选择(128);
传输协议(TCP);
伪装方式(none);
其他按照v2ray配置信息填写.
```