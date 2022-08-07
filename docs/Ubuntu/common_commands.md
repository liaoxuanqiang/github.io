# 常用命令

------

## 身份权限管理及开关机

### 1.获取用户身份命令

```bash
whoami
```

**whoami**命令可以获得当前用户名称，提示符为"**$**",则表示当前用户为普通用户，提示符为"**#**"，则表示超级用户。

### 2.su 命令

**su**命令用来切换用户身份。

```bash
su - root #-表示切换到root用户及环境
```

或

```bash
su - #可以省略root用户
```

切换用户身份后，提示符将由普通用户"**$**"变为超级用户"**#**",命令中的"**-**"表示套用所切换用户的Shell环境。

### 3.sudo 命令

如果只是想临时获得超级用户权限来完成某一操作，及临时提权，只需运行**sudo**命令

```bash
sudo snap install firefox #临时获得超级用户权限,通过snap来安装frefox浏览器 
sudo password for liaox : #输入liaox用户的密码
```

### 4.添加root用户

```bash
sudo passwd root
```

### 5.重启系统命令

```bash
sudo shutdown -r 0 #参数表示重启,0表示0秒后重启,即立即重启,这是 最为稳妥的重启方式
```

或

```bash
sudo reboot #快速重启系统
```

### 6.关机命令

```bash
sudo shutdown -h 0 #h参数表示关机,0表示0秒后关机,即立即关机,这是最为稳妥的关机方式
```

或

```bash
sudo halt #快速关机,因为文件系统越来越强大,因此可以直接关机
```

## 创建文件和目录

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

## 复制文件和目录

### 1.复制文件

在命令行中复制文件或目录可以使用**cp**命令：

```bash
cd #首先定位到Home目录
cp ./.bashrc src/ #复制当前目录下的隐藏文件bashrc到src目录下。
```

### 2.复制目录

```bash
cd /etc #将工作目录切换到etc目录 
cp profile ~ #复制profile文件到Home目录下。
```

如果要复制整个目录，则需要添加r参数，这样就可以将目录及目录下的所有文件复制到目标位置，具体操作如下：

```bash
cp -r ./src ~/Documents
```

## 浏览文本文件

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

## 移动文件和目录

使用**mv**命令可以移动文件和目录。

将文本文件**hello**移动到**src**目录：

```bash
mv hello src
```

再将**src**目录移动到**dest**目录下：

```bash
mv src dest
```

## 删除文件和目录

### 1.删除文件

```bash
rm umask027.chk
```

在命令行中删除文件需要使用**rm**命令。

### 2.删除目录

```bash
rm -r ./src
```

删除目录和复制命令**cp**类似，需要添加r参数，这样就可以将目录及该目录中的所有文件全部删除。

还有一个比较鸡肋的命令**rmdir**需要使用该命令删除目录，首先需要将该目录下的所有文件删除才能成功。
