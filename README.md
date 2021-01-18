# 萌咖大佬的一键DD脚本

## 注意:
全自动安装默认root密码:``` MoeClub.org ```,安装完成后请立即更改密码.

能够全自动重装Debian/Ubuntu/CentOS等系统.

同时提供dd安装镜像功能,例如: 全自动无救援dd安装windows系统

全自动安装CentOS时默认提供VNC功能,可使用VNC Viewer查看进度,

VNC端口为``` 1``` 或者``` 5901``` ,可自行尝试连接.(成功后VNC功能会消失.)

~~目前CentOS系统只支持任意版本重装为 CentOS 6.x 及以下版本.~~
傻瓜式一键脚本目前支持CentOS 6-8,Debian 7-10,Ubuntu 14-18,windows 7/2003/2008/2012/2016/2019，具体账号密码为：

CentOS 7 (DD) 用户名：root 密码：Pwd@CentOS 

CentOS 6 (阿里云镜像) 用户名：root 密码：MoeClub.org

CentOS 6 用户名：root 密码：MoeClub.org

Debian 7 x32 用户名：root 密码：MoeClub.org

Debian 8 x64 用户名：root 密码：MoeClub.org

Debian 9 x64 用户名：root 密码：MoeClub.org

Debian 10 x64 用户名：root 密码：cxthhhhh.com

Ubuntu 14.04x64 用户名：root 密码：MoeClub.org

Ubuntu 16.04x64 用户名：root 密码：MoeClub.org

Ubuntu 18.04x64 用户名：root 密码：MoeClub.org

萌咖Win7x64 用户名:Administrator  密码：Vicer

Win2019 By:MeowLove  密码：cxthhhhh.com

Win2016 By:MeowLove  密码：cxthhhhh.com

Win2012 R2 By:MeowLove  密码：cxthhhhh.com

Win2008 R2 By:MeowLove  密码：cxthhhhh.com

Windows 7 Vienna By:MeowLove  密码：cxthhhhh.com

Windows 2003 Vienna By:MeowLove  密码：cxthhhhh.com

Win7x32 By:老司机  用户名:Administrator  密码：Windows7x86-Chinese

Win-2003x32 By:老司机  用户名:Administrator  密码：WinSrv2003x86-Chinese

Win2008x64 By:老司机  用户名:Administrator  密码：WinSrv2008x64-Chinese

Win2012R2x64 By:老司机  用户名:Administrator  密码：WinSrv2012r2

CentOS 8 用户名：root 密码：cxthhhhh.com 推荐512M以上使用

自定义安装其他版本请使用：bash InstallNET.sh -dd '您的直连'，InstallNET.sh的具体用法请看 ## 下载及说明

特别注意:OpenVZ构架不适用.

## linux dd傻瓜式一键脚本
```
##镜像文件在OneDrive
wget -N --no-check-certificate https://raw.githubusercontent.com/x2009again/dd/master/dd-od.sh && chmod +x dd-od.sh && ./dd-od.sh

##镜像文件在GoogleDrive
wget -N --no-check-certificate https://raw.githubusercontent.com/x2009again/dd/master/dd-gd.sh && chmod +x dd-gd.sh && ./dd-gd.sh

```
## Windows to Linux 一键脚本（MoeClub大佬的脚本修改版，Debian8停止维护了，所以我改为了Debian10）
```
下载win32loader.bat，直接点击运行，重启后就会自动进入安装debian10系统，如果是非dhcp模式且无VNC的需要先定制镜像，然后指定镜像来安装为Linux，有VNC的可以在安装系统时手动设置ip等配置。

linux生成指定debian镜像示例（注意需要使用纯净的系统来操作，执行后普通用户会无法登录ssh，提示没有权限，所以建议使用临时系统来操作）：

bash InstallNET.sh -d 10 -v 64 -a --mirror 'http://ftp.debian.org/debian/' -firmware --loader

然后复制出/root/loader 下的initrd.img和vmlinuz文件到%SystemDrive%\win32-loader目录下，一般是C盘的win32-loader目录下，

root默认密码：MoeClub.org，也可以在上面的命令中加入参数-p来自定义密码

```

## 关于debian10源报错

在脚本中可以添加 --mirror 参数切换源。
目前可用的源:
```
--mirror 'http://mirrors.aliyun.com/debian/'
--mirror 'http://cpgs.fdcservers.net/debian/'
--mirror 'http://proyectos.uls.edu.sv/debian/'
--mirror 'http://debian.cabletel.com.mk/debian/'
--mirror 'http://komo.padinet.com/debian/'
--mirror 'http://www.debian.uz/debian/'
```
安装debian10 示例:
```
bash InstallNET.sh -d 10 -v 64 -a --mirror 'http://ftp.debian.org/debian/'
```
安装dd镜像 示例:
```
bash InstallNET.sh -dd "[URL]" --mirror 'http://ftp.debian.org/debian/'
```


## 确保安装了所需软件:

``` 
#Debian/Ubuntu:
apt-get install -y xz-utils openssl gawk file wget
 
#RedHat/CentOS:
yum install -y xz openssl gawk file
``` 

## 如果出现了错误,请运行:
``` 
#Debian/Ubuntu:
apt-get update
 
#RedHat/CentOS:
yum update
``` 

## 快速使用示例:
``` 	
bash <(wget --no-check-certificate -qO- 'https://raw.githubusercontent.com/x2009again/dd/master/InstallNET.sh') -d 10 -v 64 -a
``` 

## 下载及说明:
``` 
wget --no-check-certificate -qO InstallNET.sh 'https://raw.githubusercontent.com/x2009again/dd/master/InstallNET.sh' && chmod +x InstallNET.sh
``` 
```
Usage:
        bash InstallNET.sh      -d/--debian [dist-name]
                                -u/--ubuntu [dist-name]
                                -c/--centos [dist-version]
                                -v/--ver [32/i386|64/amd64]
                                --ip-addr/--ip-gate/--ip-mask
                                -apt/-yum/--mirror
                                -dd/--image
                                -a/-m
 
# dist-name: 发行版本代号
# dist-version: 发行版本号
# -apt/-yum/--mirror : 使用定义镜像
# -a/-m : 询问是否能进入VNC自行操作. -a 为不提示(一般用于全自动安装), -m 为提示.
```

## 使用示例:
```
#使用默认镜像全自动安装
bash InstallNET.sh -d 8 -v 64 -a
bash InstallNET.sh -d 9 -v 64 -a
bash InstallNET.sh -d 10 -v 64 -a
分别表示自动安装Debian 8x64  9x64 10x64
 
#使用自定义镜像全自动安装
bash InstallNET.sh -c 6.9 -v 64 -a --mirror 'http://mirror.centos.org/centos'
 
 
# 以下示例中,将X.X.X.X替换为自己的网络参数.
# --ip-addr :IP Address/IP地址
# --ip-gate :Gateway   /网关
# --ip-mask :Netmask   /子网掩码
 
#使用自定义镜像自定义网络参数全自动安装
#bash InstallNET.sh -u 16.04 -v 64 -a --ip-addr x.x.x.x --ip-gate x.x.x.x --ip-mask x.x.x.x --mirror 'http://archive.ubuntu.com/ubuntu'
 
#使用自定义网络参数全自动dd方式安装
#bash InstallNET.sh --ip-addr x.x.x.x --ip-gate x.x.x.x --ip-mask x.x.x.x -dd 'https://moeclub.org/get-win7embx86-auto'
 
#使用自定义网络参数全自动dd方式安装存储在谷歌网盘中的镜像(调用文件ID的方式)
#bash InstallNET.sh --ip-addr x.x.x.x --ip-gate x.x.x.x --ip-mask x.x.x.x -dd "$(echo "1cqVl2wSGx92UTdhOxU9pW3wJgmvZMT_J" |xargs -n1 bash <(wget --no-check-certificate -qO- 'https://moeclub.org/get-gdlink'))"
 
#使用自定义网络参数全自动dd方式安装存储在谷歌网盘中的镜像
#bash InstallNET.sh --ip-addr x.x.x.x --ip-gate x.x.x.x --ip-mask x.x.x.x -dd "$(echo "https://drive.google.com/open?id=1cqVl2wSGx92UTdhOxU9pW3wJgmvZMT_J" |xargs -n1 bash <(wget --no-check-certificate -qO- 'https://moeclub.org/get-gdlink'))"
```

## 一些可用镜像地址:
```
# 推荐使用带有 /GoogleDrive/<File_ID> 链接, 速度更快.
# 当然也可以使用自己GoogleDrive中储存的镜像,使用方式:
  https://image.moeclub.org/GoogleDrive/<File_ID>
 
# win7emb_x86.tar.gz:
  https://image.moeclub.org/GoogleDrive/1srhylymTjYS-Ky8uLw4R6LCWfAo1F3s7 
  https://image.moeclub.org/win7emb_x86.tar.gz
 
# win8.1emb_x64.tar.gz:
  https://image.moeclub.org/GoogleDrive/1cqVl2wSGx92UTdhOxU9pW3wJgmvZMT_J
  https://image.moeclub.org/win8.1emb_x64.tar.gz
```

## 一些提示:

特别注意:

萌咖提供的dd安装镜像

远程登陆账号为: ```Administrator```

远程登陆密码为: ```Vicer```

仅修改了主机名,可放心使用.(建议自己制作.)

在dd安装系统镜像时:

在你的机器上全新安装,如果你有VNC,可以看到全部过程.

在dd安装镜像的过程中,不会走进度条(进度条一直显示为0%).完成后将会自动重启.

分区界面标题一般显示为: “Starting up the partitioner“

使用谷歌网盘中储存的镜像: [无限制大小] 获取谷歌网盘文件临时直接下载链接

在全自动安装CentOS时:

如果看到 “Starting graphical installation” 或者类似表达,则表示正在安装.

正常情况下只需要耐心等待安装完成即可.

如果需要查看进度,使用VNC Viewer(或者其他VNC连接工具)

连接提示中的IP地址:端口进行连接.(端口一般为```1```或者```5901```)


### GD直连获取方法
1.下载脚本
```
wget -N --no-check-certificate https://raw.githubusercontent.com/veip007/DDWIN/master/gdlink.sh && chmod +x gdlink.sh && ./gdlink.sh
```
2.使用方法
```
#Work with share link/使用分享链接方式
gdlink 'https://drive.google.com/open?id=0B8SvBXZ3I5QMcUduTMJEanRkMzQ'

#Work with file id/使用文件ID方式
gdlink '0B8SvBXZ3I5QMcUduTMJEanRkMzQ'
 
#download with share link/使用分享链接方式直接使用wget下载链接
##可将其中./download改成自己需要的文件名或文件绝对路径
gdlink 'https://drive.google.com/open?id=0B8SvBXZ3I5QMcUduTMJEanRkMzQ' |xargs -n1 wget -c -O ./download
```



转载于萌咖https://moeclub.org/2018/04/03/603/
