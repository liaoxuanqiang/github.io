# Ubuntu 系统配置 Ubuntu system configuration

------

## 修改软件源并更新系统软件

### 1.备份软件源配置文件

```shell
sudo cp -a /etc/apt/sources.list /etc/apt/sources.list.bak
```

### 2.修改sources.list文件

将 http://archive.ubuntu.com 和 http://security.ubuntu.com 替换成 http://repo.huaweicloud.com 可以参考如下命令：

```shell
sudo sed -i "s@http://.\*archive.ubuntu.com@http://repo.huaweicloud.com@g" /etc/apt/sources.list

sudo sed -i "s@http://.\*security.ubuntu.com@http://repo.huaweicloud.com@g" /etc/apt/sources.list
```

也可以手动修改sources.list文件

```shell
sudo vim /etc/apt/sources.list
```

### 3.更新系统软件索引

```shell
sudo apt-get update
```

### 4.更新系统软件

```shell
sudo apt-get upgrade
```

## 挂载exfat格式的U盘、移动硬盘

### 1.安装exfat的支持软件

```shell
sudo apt-get install exfat-fuse
```

### 2.重启系统

```shell
sudo shutdown -r now
```

### 3.插上U盘、移动硬盘

### 4.查看磁盘信息

```shell
sudo fdisk -l 
```

### 5.挂载U盘、移动硬盘

```shell
cd /mnt
sudo mkdir user_usb   #创建挂载目录
sudo mount /dev/sdb1 /mnt/user_usb  #执行挂载sdb1分区到user_usb目录
```

### 6.执行对挂载U盘移动硬盘的读写操作

### 7.卸载

```shell
sudo umount /mnt/user_usb  #完成操作后需要先执行卸载命令再将U盘、移动硬盘拔出
```

## 搭建samba服务

### 1.安装软件

```shell
sudo apt update
sudo apt install samba
```

### 2.配置

```shell
vim /etc/samba/smb.conf #修改配置文件
```

文件底部添加配置

```shell
[share]
    path = /home/username/share
    read only = no
    browsable = yes
```

### 3.配置权限

```shell
chmod 777 /home/username/share
sudo smbpasswd -a username #添加用户
```

\*username是要添加的用户名，提示输入密码即可

### 4.运行

```shell
sudo service smbd restart
```

## 配置DNS

### 1.查看端口占用情况，看看 53 端口是不是被 `systemd-resolved` 占用

```
sudo netstat -nultp
```

### 2.先停用 systemd-resolved 服务

```
systemctl stop systemd-resolved
```

### 3.编辑 /etc/systemd/resolved.conf 文件

```
vi /etc/systemd/resolved.conf
```

### 4.换下面说明更改，然后按一下“esc”键，再输入“:wq”（不要输入引号），回车保存即可。

```
[Resolve]
DNS=8.8.8.8  #取消注释，增加dns
#FallbackDNS=
#Domains=
#LLMNR=no
#MulticastDNS=no
#DNSSEC=no
#Cache=yes
DNSStubListener=no  #取消注释，把yes改为no
```

### 5.最后运行下面命令即可

```
ln -sf /run/systemd/resolve/resolv.conf /etc/resolv.conf
```

### 6、查看结果

```
systemd-resolve --status
```

## 刷新/删除DNS缓存

如果你没有在 Linux 下安装和运行 Systemd-Resolved、DNSMasq、Nscd 缓存服务，那就没有操作系统级的 DNS 缓存，不同的 Linux 发行版在刷新 DNS 缓存上方法是不同的。

### 1.刷新 Systemd Resolved 缓存

Ubuntu 18.04 系统是使用 Systemd Resolved 服务来缓存 DNS 的，所以可以运行以下命令确定该服务是否运行：

```
sudo systemctl is-active systemd-resolved.service
```

如果服务运行，则会看到返回的活动状态信息，否则只会看到非活动状态。

删除 Systemd Resolved DNS 缓存的方法，运行以下命令：

```
sudo systemd-resolve --flush-caches
```

### 2.刷新 DNSMasq 缓存

如果你在 Ubuntu 18.04 下使用 DNSMasq 作为缓存服务器，要删除 DNS 缓存，请运行以下命令：

```
sudo systemctl restart dnsmasq.service
```

### 3.刷新 Nscd 缓存

参考：《[CentOS 优化 DNS 设置：配置冗余 DNS 并开启 NSCD 缓存服务教程](https://oldtang.com/3317.html)》。

如果使用了 Nscd，删除 DNS 缓存只需要运行以下命令：

```
sudo systemctl restart nscd.service
```

或者运行：

```
sudo service nscd restart
```
