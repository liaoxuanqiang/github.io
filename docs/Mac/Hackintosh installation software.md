# Hackintosh 安装软件

Hackintosh installation software

------



#### iTerm2

#### Homebrew

##### 安装

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"  # 安装命令
```

##### 设置代理

```bash
export https_proxy=http://127.0.0.1:7890 http_proxy=http://127.0.0.1:7890 all_proxy=socks5://127.0.0.1:7890 # ClashX 代理示例
```

##### brew 常用命令与软件

```bash
brew update # 更新 Homebrew
brew search [关键词] # 搜索相关的包
rew info [软件名]   # 查看包的信息
brew list # 查看已安装的包
brew upgrade [软件名] # 更新某个软件
brew cleanup # 清理所有软件的旧版
brew uninstall [软件名] # 卸载某个软件
brew install iproute2mac # ip 命令 查看ip地址很方便
```

##### brew services 命令

```bash
brew services list： # 查看所有服务 
brew services run [服务名] # 单次运行某个服务
brew services start [服务名] # 运行某个服务，并设置开机自动运行
brew services stop [服务名] # 停止某个服务
brew services restart # 重启某个服务
```

##### brew 常用配置

```bash
brew install iproute2mac # ip 命令 查看ip地址很方便
brew install cask # 安装 brew-cask
brew install qlmarkdown # 空格预览 markdown
brew install syntax-highlight # 空格预览代码文件
```



#### Oh My Zsh

##### 安装

```bash
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)" # 安装卡的话就挂代理
```

##### 主题

```bash
vim ~/.zshrc #修改配置文件

ZSH_THEME=robbyrussell #在配置文件中修改此行（"="后面填写自己的主题）
ls -l ~/.oh-my-zsh/themes # 查看自带的主题
```

##### 插件

###### autojump

```bash
brew install autojump

vim ~/.zshrc 
plugins=(其他的插件 autojump) #在 ~/.zshrc 中配置此行
```



#### proxychains-ng

##### 安装配置

```bash
brew install proxychains-ng # 安装
vim /usr/local/etc/proxychains.conf # 配置文件
socks5 127.0.0.1 7890 #修改配置文件结尾的 socks4 127.0.0.1 9095
```

##### 常用命令

```bash
proxychains4 curl https://www.google.com.hk # 代理终端基本示例
proxychains4 -q /bin/bash # 全局代理 bash shell
proxychains4 -q /bin/zsh # 全局代理 zsh shell
```



#### Vim

```bash
vim ~/.vimrc #在用户目录下新建一个 vim 的配置文件

编辑内容如下：
set nu                " 显示行号
colorscheme desert    " 颜色显示方案
syntax on             " 打开语法高亮

ls /usr/share/vim/vim*/colors #查看其他自带的配色方案
```



#### Git

#### Python

##### Python2

##### Python3

##### pyenv

###### 安装配置

```bash
brew install pyenv # 安装pyenv

vim ~/.zshrc #修改配置文件
alias brew='env PATH="${PATH//$(pyenv root)\/shims:/}" brew' #将此内容写入到 ~/.zshrc 配置文件
```

###### 版本安装

```bash
pyenv versions # 查看已经安装的Python版本
pyenv version # 查看当前的 Python 版本
pyenv install -l # 查看可安装的版本

pyenv install pypy3.8-7.3.7 # 安装与卸载 pypy3.8-7.3.7
pyenv uninstall pypy3.8-7.3.7
所安装的版本都在 ~/.pyenv/versions目录下
```

###### 版本切换

```bash
pyenv global <python版本> # global 全局设置 一般不建议改变全局设置
pyenv shell <python版本> # shell 会话设置 只影响当前的shell会话

pyenv shell --unset # 取消 shell 会话的设置
pyenv local <python版本> # local 本地设置 只影响所在文件夹
pyenv 的 global、local、shell 的优先级关系是：shell > local > global
```



##### Node.js

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash # 安装 nvm

zsh
nvm --version # 查看版本信息
0.39.1
nvm version  # 查看当前 node 的版本
nvm install stable # 安装最新稳定版 node
nvm ls-remote # 列出所有远程服务器的版本
nvm install v12.22.9 # 安装指定版本
nvm install <version>

nvm ls # 列出所有已安装的版本
nvm uninstall <version> # 卸载指定的版本
nvm use <version> # 切换使用指定的版本node
nvm current # 显示当前的版本
```

