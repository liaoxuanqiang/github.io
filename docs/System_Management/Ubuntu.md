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



## 安装软件

## 系统配置

