# Ubuntu 软件包命令
Ubuntu package commands
------

## apt命令

<!-- tabs:start -->

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

<!-- tabs:end -->

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