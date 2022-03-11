# Ubuntu 使用管理

## 相关资源

## 常用命令

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

## 安装软件

## apt命令

### 1.搜索软件包

```bash
sudo apt search neofetch #搜索软件包
sudo apt show neofetch #显示软件包的详细信息
sudo apt list neofetch #列出包含条件的包（已安装、可升级等）
```

### 2.安装/卸载软件包

```bash
sudo apt install neofetch #安装软件包，常用参数-y表示安装无须确认，如：sudo apt install-y neofetch
sudo apt remove neofetch #卸载软件包
sudo apt purge neofetch #删除软件包和相关配置文件
```

### 3.升级软件包

```bash
sudo apt update #更新存储库索引，install前必须运行
sudo apt upgrade #升级所有可升级的软件包
sudo apt full-upgrade #升级软件包并自动解决依赖关系
sudo apt edit-sources #编辑软件源列表 
```

### 4.清理软件包

```bash
sudo apt autoclean #自动清除不需要的包
sudo apt autoremove #自动删除不需要的包
```

在使用apt命令时，可能看到如下内容：

WARNING: apt does not have a stable CLI interface. Use with caution in scripts. （警告：apt命令不是很稳定，在Shell脚本中使用请小心。）

## apt-cache/apt-get 命令

由于**apt-cache** 用于搜索软件，而**apt-get**用于软件管理，如安装、卸载、升级等操作，故这两个命令通常一同出现。

### 1.搜索软件包

```bash
sudo apt-cache search neofetch #搜索软件包
sudo apt-cache show neofetch #显示软件包的详细信息
```

### 2.安装/卸载软件包

```bash
sudo apt-get install neofetch #安装软件包
sudo apt-get remove neofetch #卸载软件包
sudo apt-get purge neofetch #删除软件包和相关配置文件
```

### 3.升级软件包

```
sudo apt-get update #更新存储索引，安装前必须运行
sudo apt-get upgrade #升级所有可升级的软件包
```

**apt-get update**和**apt-get-upgrade**的最大区别是，**update**仅同步更新软件列表，而**upgrade**则根据列表更新软件本身。

### 4.清理软件包

```bash
sudo apt-get autoclean #自动清除不需要的包
sudo apt-get autoremove #自动删除不需要的包
```

## aptitude 命令

在实际应用中，要高效使用**aptitude**，通常将其作为命令行工具来使用，首先使用如下命令来安装：

### aptitude安装

```bash
sudo apt update
sudo apt install -y aptitude
```

运行如下命令启动**aptitude**文本界面：

```bash
sudo aptitude
```

### **aptitude**使用命令:

#### 1.搜索软件包

```
sudo aptitude search neofetch
```

#### 2.安装软件包

```bash
sudo aptitude install neofetch
```

#### 3.删除软件包

```bash
sudo aptitude remove neofetch #普通删除
sudo aptitude purge neofech #彻底删除
```

#### 4.更新软件仓库列表

```bash
sudo aptitude update #更新存储库索引，安装前必须运行
```

#### 5.更新软件包

```bash
sudo aptitude upgrade
```

#### 6.清理无用软件包

```bash
sudo aptitude clean
sudo aptitude autoclean
```

## snap 命令

snap软件包格式是一种由Ubuntu主导的Linux的通用软件包格式，是为了解决Linux软件复杂的依赖关系的软件包，其思路类似于Mac OS的pkg软件包，用空间换便捷，和DEB软件包由本质区别，其将程序所需要的依赖全部打入一个包，通过snap命令进行安装、卸载、和更新等操作。

snap格式软件包应用商店：[https://snapcraft.io/store](https://snapcraft.io/store)

可以使用Find snaps功能搜索仓库，迅速找到所需要的程序。

### snap使用命令

#### 1.搜索软件包

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

#### 2.安装/卸载软件包

安装软件包：

```bash
sudo snap install firefox
```

卸载软件包：

```
sudo snap remove firefox
```

#### 3.升级软件包

升级软件包：

```
sudo snap refresh
```

撤销升级：

```
sudo snap revert
```

#### 4.获得最近变更：

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

## tasksel 命令

taskel可以一次性安装被称为任务（task）的一组软件包，执行一组预定义的安装指令集，如安装LAMP组合、各种桌面环境等，功能强大但使用异常简单。

### tasksel安装

```bash
sudo apt update
sudo apt install -y tasksel
```

### tasksel使用命令

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

## 系统配置

