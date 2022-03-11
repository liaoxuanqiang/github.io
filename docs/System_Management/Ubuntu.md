# Ubuntu 使用管理

------

## 相关资源

### Ubuntu 镜像

#### LTS Releases

- [Ubuntu 20.04.3 LTS (Focal Fossa)](http://releases.ubuntu.com/focal/)
- [Ubuntu 18.04.6 LTS (Bionic Beaver)](http://releases.ubuntu.com/bionic/)

#### Interim Releases

- [Ubuntu 21.10 (Impishell Indri)](http://releases.ubuntu.com/impishell/)
- [Ubuntu 21.04 (Hirsute Hippo)](http://releases.ubuntu.com/hirsute/)

### 开源镜像站

- [USTC open source software mirror](https://mirrors.ustc.edu.cn/)
- [华为开源镜像站](https://www.huaweicloud.com/product/mirrors.html?utm_source=3.baidu.com&utm_medium=organic&utm_adplace=kapian&ticket=ST-284735-qBnErkcWHqKY2S2UabAESk14-sso)
- [阿里云镜像站](https://developer.aliyun.com/mirror/)
- [网易开源镜像站](https://mirrors.163.com/)
- [清华大学开源软件镜像站](https://mirrors.tuna.tsinghua.edu.cn/)

------

## 常用命令

### 身份权限管理及开关机

#### 1.获取用户身份命令

```bash
whoami
```

**whoami**命令可以获得当前用户名称，提示符为"**$**",则表示当前用户为普通用户，提示符为"**#**"，则表示超级用户。

#### 2.su 命令

**su**命令用来切换用户身份。

```bash
su - root #-表示切换到root用户及环境
```

或

```bash
su - #可以省略root用户
```

切换用户身份后，提示符将由普通用户"**$**"变为超级用户"**#**",命令中的"**-**"表示套用所切换用户的Shell环境。

#### 3.sudo 命令

如果只是想临时获得超级用户权限来完成某一操作，及临时提权，只需运行**sudo**命令

```bash
sudo snap install firefox #临时获得超级用户权限,通过snap来安装frefox浏览器 
sudo password for liaox : #输入liaox用户的密码
```

#### 4.添加root用户

```bash
sudo passwd root
```

#### 5.重启系统命令

```bash
sudo shutdown -r 0 #参数表示重启,0表示0秒后重启,即立即重启,这是 最为稳妥的重启方式
```

或

```bash
sudo reboot #快速重启系统
```

#### 6.关机命令

```bash
sudo shutdown -h 0 #h参数表示关机,0表示0秒后关机,即立即关机,这是最为稳妥的关机方式
```

或

```bash
sudo halt #快速关机,因为文件系统越来越强大,因此可以直接关机
```

### 创建文件和目录

在命令行中创建一个文件可以使用**touch**命令：

```bash
touch umask027.chk
```

如果要创建一个有内容的文本文件可以使用如下命令：

```bash
echo "Hello world" >hello
```

创建目录可以使用mkdir命令：

```bash
mkdir src dest
```

使用上述命令将一次创建两个目录--**src**和**dest**。

### 复制文件和目录

#### 1.复制文件

在命令行中复制文件或目录可以使用**cp**命令：

```bash
cd #首先定位到Home目录
cp ./.bashrc src/ #复制当前目录下的隐藏文件bashrc到src目录下。
```

#### 2.复制目录

```bash
cd /etc #将工作目录切换到etc目录 
cp profile ~ #复制profile文件到Home目录下。
```

如果要复制整个目录，则需要添加r参数，这样就可以将目录及目录下的所有文件复制到目标位置，具体操作如下：

```bash
cp -r ./src ~/Documents
```

### 浏览文本文件

要在命令中浏览ASCII文件，如源代码、Shell脚本等，可以使用**cat**命令：

```bash
cat README #一次性显示所有文本
```

或

```bash
more README #翻页显示文本，但只能向下翻页
```

或

```bash
less README #翻页显示文本，可上下翻页
```

### 移动文件和目录

使用**mv**命令可以移动文件和目录。

将文本文件**hello**移动到**src**目录：

```bash
mv hello src
```

再将**src**目录移动到**dest**目录下：

```bash
mv src dest
```

### 删除文件和目录

#### 1.删除文件

```bash
rm umask027.chk
```

在命令行中删除文件需要使用**rm**命令。

#### 2.删除目录

```bash
rm -r ./src
```

删除目录和复制命令**cp**类似，需要添加r参数，这样就可以将目录及该目录中的所有文件全部删除。

还有一个比较鸡肋的命令**rmdir**需要使用该命令删除目录，首先需要将该目录下的所有文件删除才能成功。

------

## 安装软件

### apt命令

<!-- tabs:start -->

#### 1.搜索软件包

```bash
sudo apt search neofetch #搜索软件包
sudo apt show neofetch #显示软件包的详细信息
sudo apt list neofetch #列出包含条件的包（已安装、可升级等）
```

#### 2.安装/卸载软件包

```bash
sudo apt install neofetch #安装软件包，常用参数-y表示安装无须确认，如：sudo apt install-y neofetch
sudo apt remove neofetch #卸载软件包
sudo apt purge neofetch #删除软件包和相关配置文件
```

#### 3.升级软件包

```bash
sudo apt update #更新存储库索引，install前必须运行
sudo apt upgrade #升级所有可升级的软件包
sudo apt full-upgrade #升级软件包并自动解决依赖关系
sudo apt edit-sources #编辑软件源列表 
```

#### 4.清理软件包

```bash
sudo apt autoclean #自动清除不需要的包
sudo apt autoremove #自动删除不需要的包
```

<!-- tabs:end -->

在使用apt命令时，可能看到如下内容：

WARNING: apt does not have a stable CLI interface. Use with caution in scripts. （警告：apt命令不是很稳定，在Shell脚本中使用请小心。）

### apt-cache/apt-get 命令

由于**apt-cache** 用于搜索软件，而**apt-get**用于软件管理，如安装、卸载、升级等操作，故这两个命令通常一同出现。

#### 1.搜索软件包

```bash
sudo apt-cache search neofetch #搜索软件包
sudo apt-cache show neofetch #显示软件包的详细信息
```

#### 2.安装/卸载软件包

```bash
sudo apt-get install neofetch #安装软件包
sudo apt-get remove neofetch #卸载软件包
sudo apt-get purge neofetch #删除软件包和相关配置文件
```

#### 3.升级软件包

```
sudo apt-get update #更新存储索引，安装前必须运行
sudo apt-get upgrade #升级所有可升级的软件包
```

**apt-get update**和**apt-get-upgrade**的最大区别是，**update**仅同步更新软件列表，而**upgrade**则根据列表更新软件本身。

#### 4.清理软件包

```bash
sudo apt-get autoclean #自动清除不需要的包
sudo apt-get autoremove #自动删除不需要的包
```

### aptitude 命令

在实际应用中，要高效使用**aptitude**，通常将其作为命令行工具来使用，首先使用如下命令来安装：

#### aptitude安装

```bash
sudo apt update
sudo apt install -y aptitude
```

运行如下命令启动**aptitude**文本界面：

```bash
sudo aptitude
```

#### **aptitude**使用命令:

##### 1.搜索软件包

```
sudo aptitude search neofetch
```

##### 2.安装软件包

```bash
sudo aptitude install neofetch
```

##### 3.删除软件包

```bash
sudo aptitude remove neofetch #普通删除
sudo aptitude purge neofech #彻底删除
```

##### 4.更新软件仓库列表

```bash
sudo aptitude update #更新存储库索引，安装前必须运行
```

##### 5.更新软件包

```bash
sudo aptitude upgrade
```

##### 6.清理无用软件包

```bash
sudo aptitude clean
sudo aptitude autoclean
```

### snap 命令

snap软件包格式是一种由Ubuntu主导的Linux的通用软件包格式，是为了解决Linux软件复杂的依赖关系的软件包，其思路类似于Mac OS的pkg软件包，用空间换便捷，和DEB软件包由本质区别，其将程序所需要的依赖全部打入一个包，通过snap命令进行安装、卸载、和更新等操作。

snap格式软件包应用商店：[https://snapcraft.io/store](https://snapcraft.io/store)

可以使用Find snaps功能搜索仓库，迅速找到所需要的程序。

#### snap使用命令

##### 1.搜索软件包

搜索软件包：

```
sudo snap find/search firefox
```

获得所安装软件包最为详尽的信息：

```bash
sudo snap info firefox
```

列出已安装软件包的详细信息：

```bash
sudo snap list firefox
```

##### 2.安装/卸载软件包

安装软件包：

```bash
sudo snap install firefox
```

卸载软件包：

```
sudo snap remove firefox
```

##### 3.升级软件包

升级软件包：

```
sudo snap refresh
```

撤销升级：

```
sudo snap revert
```

##### 4.获得最近变更：

```
snap change
```

列出所有得snap应用可以使用如下命令：

```
snap find
```

以**htop**为例，搜索**htop**应用程序，可以使用如下命令：

```
snap find htop
Name  version  Developer  Notes  Summary
```

可以使用如下命令安装snap软件包：

```
sudo snap install htop
```

**snap**默认目录是**/snap.**将下载的安装文件挂载到该目录下并创建挂载点，然后复制文件到指定位置。

### tasksel 命令

taskel可以一次性安装被称为任务（task）的一组软件包，执行一组预定义的安装指令集，如安装LAMP组合、各种桌面环境等，功能强大但使用异常简单。

#### tasksel安装

```bash
sudo apt update
sudo apt install -y tasksel
```

#### tasksel使用命令

```
sudo apt update
tasksel --list-task #列出可选的软件包
u manual    Manual package selection
```

运行如下命令安装任务：

```
sudo tasksel install lubuntu-core
```

或

```bash
sudo tasksel
```

然后在弹出的文本界面中通过上下方向键选择一个或多个安装对象，选好后按Tab键将光标移至OK处，按Enter键后即可开始安装。

运行如下命令卸载：

```bash
sudo tasksel remove lubuntu-core
```

------

## 系统配置

### 修改软件源并更新系统软件

#### 1.备份软件源配置文件

```shell
sudo cp -a /etc/apt/sources.list /etc/apt/sources.list.bak
```

#### 2.修改sources.list文件

将 http://archive.ubuntu.com 和 http://security.ubuntu.com 替换成 http://repo.huaweicloud.com 可以参考如下命令：

```shell
sudo sed -i "s@http://.\*archive.ubuntu.com@http://repo.huaweicloud.com@g" /etc/apt/sources.list

sudo sed -i "s@http://.\*security.ubuntu.com@http://repo.huaweicloud.com@g" /etc/apt/sources.list
```

也可以手动修改sources.list文件

```shell
sudo vim /etc/apt/sources.list
```

#### 3.更新系统软件索引

```shell
sudo apt-get update
```

#### 4.更新系统软件

```shell
sudo apt-get upgrade
```

### 挂载exfat格式的U盘、移动硬盘

#### 1.安装exfat的支持软件

```shell
sudo apt-get install exfat-fuse
```

#### 2.重启系统

```shell
sudo shutdown -r now
```

#### 3.插上U盘、移动硬盘

#### 4.查看磁盘信息

```shell
sudo fdisk -l 
```

#### 5.挂载U盘、移动硬盘

```shell
cd /mnt
sudo mkdir user_usb   #创建挂载目录
sudo mount /dev/sdb1 /mnt/user_usb  #执行挂载sdb1分区到user_usb目录
```

#### 6.执行对挂载U盘移动硬盘的读写操作

#### 7.卸载

```shell
sudo umount /mnt/user_usb  #完成操作后需要先执行卸载命令再将U盘、移动硬盘拔出
```

### 搭建samba服务

#### 1.安装软件

```shell
sudo apt update
sudo apt install samba
```

#### 2.配置

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

#### 3.配置权限

```shell
chmod 777 /home/username/share
sudo smbpasswd -a username #添加用户
```

\*username是要添加的用户名，提示输入密码即可

#### 4.运行

```shell
sudo service smbd restart
```

### 配置DNS

#### 1.查看端口占用情况，看看 53 端口是不是被 `systemd-resolved` 占用

```
sudo netstat -nultp
```

#### 2.先停用 systemd-resolved 服务

```
systemctl stop systemd-resolved
```

#### 3.编辑 /etc/systemd/resolved.conf 文件

```
vi /etc/systemd/resolved.conf
```

#### 4.换下面说明更改，然后按一下“esc”键，再输入“:wq”（不要输入引号），回车保存即可。

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

#### 5.最后运行下面命令即可

```
ln -sf /run/systemd/resolve/resolv.conf /etc/resolv.conf
```

#### 6、查看结果

```
systemd-resolve --status
```

### 刷新/删除DNS缓存

如果你没有在 Linux 下安装和运行 Systemd-Resolved、DNSMasq、Nscd 缓存服务，那就没有操作系统级的 DNS 缓存，不同的 Linux 发行版在刷新 DNS 缓存上方法是不同的。

#### 1.刷新 Systemd Resolved 缓存

Ubuntu 18.04 系统是使用 Systemd Resolved 服务来缓存 DNS 的，所以可以运行以下命令确定该服务是否运行：

```
sudo systemctl is-active systemd-resolved.service
```

如果服务运行，则会看到返回的活动状态信息，否则只会看到非活动状态。

删除 Systemd Resolved DNS 缓存的方法，运行以下命令：

```
sudo systemd-resolve --flush-caches
```

#### 2.刷新 DNSMasq 缓存

如果你在 Ubuntu 18.04 下使用 DNSMasq 作为缓存服务器，要删除 DNS 缓存，请运行以下命令：

```
sudo systemctl restart dnsmasq.service
```

#### 3.刷新 Nscd 缓存

参考：《[CentOS 优化 DNS 设置：配置冗余 DNS 并开启 NSCD 缓存服务教程](https://oldtang.com/3317.html)》。

如果使用了 Nscd，删除 DNS 缓存只需要运行以下命令：

```
sudo systemctl restart nscd.service
```

或者运行：

```
sudo service nscd restart
```
