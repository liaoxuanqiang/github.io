# Docker 安装配置

Docker installation configuration

------

Docker 官网：[https://www.docker.com](https://www.docker.com/)

Github Docker 源码：https://github.com/docker/docker-ce

## Install Docker

### Windwos

手动下载[Docker Desktop for Windows](https://docs.docker.com/desktop/install/windows-install/)安装或：

```powershell
winget install Docker.DockerDesktop
docker --version #检查Docker版本
docker run hello-world #运行容器
```

### Mac

手动下载[Docker Desktop for Mac](https://docs.docker.com/desktop/install/mac-install/)安装或：

```bash
brew install --cask --appdir=/Applications docker
docker --version #检查Docker版本
docker info #查看配置信息
```

### Ubuntu

```bash
sudo apt update #更新软件包索引
sudo apt install apt-transport-https ca-certificates curl gnupg-agent software-properties-common #安装依赖软件

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add - # 导入源仓库的 GPG key
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" #将 Docker APT 软件源添加到系统

sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io #安装最新可用版
sudo systemctl status docker #验证安装
```

### 卸载 Docker

运行下面的命令停止所有正在运行的容器，并且移除所有的 docker 对象：

```bash
docker container stop $(docker container ls -aq)
docker system prune -a --volumes
```

现在你可以使用`apt`像卸载其他软件包一样来卸载 Docker：

```bash
sudo apt purge docker-ce
sudo apt autoremove
```

### Docker 软件源

```
阿里云 https://8nvn6pbc.mirror.aliyuncs.com
腾讯云 https://mirror.ccs.tencentyun.com
华为云 https://05f073ad3c0010ea0f4bc00b7105ec20.mirror.swr.myhuaweicloud.com
Docker中国 https://registry.docker-cn.com
网易 http://hub-mirror.c.163.com daocloud http://f1361db2.m.daocloud.io
中国科技大学 https://docker.mirrors.ustc.edu.cn
```