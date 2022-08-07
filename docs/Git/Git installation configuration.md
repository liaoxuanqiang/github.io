# Git 安装配置

Git Install configuration

------



## Install configuration

### Windows

```powershell
git --version #检查版本信息
winget install --id Git.Git -e --source winget #使用winget tool工具安装Git

git config --global user.email "liaoxuanqiang@live.com" # 配置邮箱
git config --global user.name "liaoxuanqiang" # 配置用户名
ssh-keygen -t rsa -C "liaoxuanqiang@live.com" # 创建ssh key
cat .ssh/id_rsa.pub # 查看.ssh/id_rsa.pub文件并复制key,在GitHub设置中添加ssh key
ssh -T git@github.com # 链接验证
```

#### Mac

```bash
brew install git #使用Homebrew安装Git
brew install git-gui #使用Homebrew安装 git-gui
或者直接安装Xcode

git config --global user.email "liaoxuanqiang@live.com" # 配置邮箱
git config --global user.name "liaoxuanqiang" # 配置用户名
ssh-keygen -t rsa -C "liaoxuanqiang@live.com" # 创建ssh key
cat .ssh/id_rsa.pub # 查看.ssh/id_rsa.pub文件并复制key,在GitHub设置中添加ssh key
ssh -T git@github.com # 链接验证
```

#### Debian&Ubuntu

```bash
apt-get install git #Ubuntu安装Git命令

add-apt-repository ppa:git-core/ppa 
apt update; apt install git

git config --global user.email "liaoxuanqiang@live.com" # 配置邮箱
git config --global user.name "liaoxuanqiang" # 配置用户名
ssh-keygen -t rsa -C "liaoxuanqiang@live.com" # 创建ssh key
cat .ssh/id_rsa.pub # 查看.ssh/id_rsa.pub文件并复制key,在GitHub设置中添加ssh key
ssh -T git@github.com # 链接验证
```



## Configure proxy

```bash
git config --global http.proxy 'http://127.0.0.1:7890' #设置理端口为7890
git config --global https.proxy 'http://127.0.0.1:7890'
git config --global http.proxy 'socks5://127.0.0.1:7890' #设置socks5代理端口为7890
git config --global https.proxy 'socks5://127.0.0.1:7890'

git config --global --unset http.proxy #取消设置git代理
git config --global --unset https.proxy

git config --global --get http.proxy #查看Git代理设置
git config --global --get https.proxy

cat ~/.gitconfig # 查看git配置
git config -l # 或者也可以这样查看git的配置
```