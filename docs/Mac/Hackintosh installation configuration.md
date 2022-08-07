## Hackintosh 安装配置

### 1.下载 Mac OS 镜像

- [macOS Monterey 12.x](https://github.com/liaoxuanqiang/System-use-management/blob/main/Mac OS)
- [macOS Big Sur 11.6.x](https://github.com/liaoxuanqiang/System-use-management/blob/main/Mac OS)
- [macOS Catalina 10.15.x](https://github.com/liaoxuanqiang/System-use-management/blob/main/Mac OS)

### 2.创建 USB 安装盘

- [Etcher](https://www.balena.io/etcher/)
- [TransMAC](https://www.acutesystems.com/scrtm.htm)

### 3.下载 Intel NUC10 Hackintosh EFI

##### OpenCore EFI

- [`Hackintosh EFI` Intel NUC10](https://github.com/hackintosh-efi/intel-nuc10)
- [`Pierpaolo` INTEL-NUC10i5FNH](https://github.com/pierpaolodimarzo/INTEL-NUC10i5FNH)
- [`MacKonsti` nuc10i7fnh](https://github.com/mackonsti/nuc10i7fnh)
- [OpenCore Sanity Checker](https://opencore.slowgeek.com/)

### 4.覆盖 USB 安装盘的EFI文件

### 5.修改 BIOS 设置

```
-SATA Mode Selection -> AHCI
-Secure Boot -> Disabled
```

### 6.Install Hackintosh

- 

## 系统优化设置

#### 1.Remove 4-digit password restriction

- ```
  pwpolicy -clearaccountpolicies # 取消4位数密码限制 
  passwd # 更改密码
  ```

#### 2.Allows to install apps from any source

- ```
  sudo spctl --master-disable # APP安装开启任何来源
  ```

#### 3.Modify hostname and share name

- ```
  sudo scutil --set HostName {自定义主机名} # 修改主机名
  sudo scutil --set ComputerName {自定义电脑名} # 修改共享名称
  ```

#### 4.Install Xcode Command Line Tools

- ```
  xcode-select --install # 安装 xcode 命令行工具
  ```

#### 5.Decreased Dock Response Time

- ```
  defaults write com.apple.dock autohide-time-modifier -float 0.5 && killall Dock # 设置启动坞动画时间设置为 0.5 秒
  defaults write com.apple.dock autohide-delay -int 0 && killall Dock # 设置启动坞响应时间最短
  ```

- ```
  defaults delete com.apple.dock autohide-time-modifier && killall Dock # 恢复启动坞默认动画时间
  defaults delete com.apple.Dock autohide-delay && killall Dock # 恢复默认启动坞响应时间
  ```

#### 6.Modify the number of launchpad rows and columns

- ```
  defaults write com.apple.dock springboard-columns -int 9 # 设置列数为 9
  defaults write com.apple.dock springboard-rows -int 6 # 设置行数为 6
  killall Dock # 重启 Dock 生效
  ```

- ```
  defaults write com.apple.dock springboard-rows Default # 恢复默认的列数
  defaults write com.apple.dock springboard-columns Default # 恢复默认的行数
  killall Dock # 重启 Dock 生效
  ```

### Development deployment

#### 1.Install and configure [Git](https://git-scm.com/download/mac)

- ```
  brew install git #使用Homebrew安装Git
  brew install git-gui #使用Homebrew安装 git-gui
  或者直接安装Xcode
  
  git config --global user.email "liaoxuanqiang@live.com" # 配置邮箱
  git config --global user.name "liaoxuanqiang" # 配置用户名
  ssh-keygen -t rsa -C "liaoxuanqiang@live.com" # 创建ssh key
  cat .ssh/id_rsa.pub # 查看.ssh/id_rsa.pub文件并复制key,在GitHub设置中添加ssh key
  ssh -T git@github.com # 链接验证
  ```

#### 2.Install [VSCode](https://code.visualstudio.com/) and add plugins

#### 3.Configure proxy

- ```
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

------

## 软件安装

#### iTerm2

#### Homebrew

##### 安装

- ```
  /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"  # 安装命令
  ```

##### 设置代理

- ```
  export https_proxy=http://127.0.0.1:7890 http_proxy=http://127.0.0.1:7890 all_proxy=socks5://127.0.0.1:7890 # ClashX 代理示例
  ```

##### brew 常用命令与软件

- ```
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

- ```
  brew services list： # 查看所有服务 
  brew services run [服务名] # 单次运行某个服务
  brew services start [服务名] # 运行某个服务，并设置开机自动运行
  brew services stop [服务名] # 停止某个服务
  brew services restart # 重启某个服务
  ```

##### brew 常用配置

- ```
  brew install iproute2mac # ip 命令 查看ip地址很方便
  brew install cask # 安装 brew-cask
  brew install qlmarkdown # 空格预览 markdown
  brew install syntax-highlight # 空格预览代码文件
  ```

#### Oh My Zsh

##### 安装

- ```
  sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)" # 安装卡的话就挂代理
  ```

##### 主题

- ```
  vim ~/.zshrc #修改配置文件
  
  ZSH_THEME=robbyrussell #在配置文件中修改此行（"="后面填写自己的主题）
  ls -l ~/.oh-my-zsh/themes # 查看自带的主题
  ```

##### 插件

###### autojump

- ```
  brew install autojump
  
  vim ~/.zshrc 
  plugins=(其他的插件 autojump) #在 ~/.zshrc 中配置此行
  ```

#### proxychains-ng

##### 安装配置

- ```
  brew install proxychains-ng # 安装
  vim /usr/local/etc/proxychains.conf # 配置文件
  socks5 127.0.0.1 7890 #修改配置文件结尾的 socks4 127.0.0.1 9095
  ```

##### 常用命令

- ```
  proxychains4 curl https://www.google.com.hk # 代理终端基本示例
  proxychains4 -q /bin/bash # 全局代理 bash shell
  proxychains4 -q /bin/zsh # 全局代理 zsh shell
  ```

#### Vim

- ```
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

- ```
  brew install pyenv # 安装pyenv
  
  vim ~/.zshrc #修改配置文件
  alias brew='env PATH="${PATH//$(pyenv root)\/shims:/}" brew' #将此内容写入到 ~/.zshrc 配置文件
  ```

###### 版本安装

- ```
  pyenv versions # 查看已经安装的Python版本
  pyenv version # 查看当前的 Python 版本
  pyenv install -l # 查看可安装的版本
  
  pyenv install pypy3.8-7.3.7 # 安装与卸载 pypy3.8-7.3.7
  pyenv uninstall pypy3.8-7.3.7
  所安装的版本都在 ~/.pyenv/versions目录下
  ```

###### 版本切换

- ```
  pyenv global <python版本> # global 全局设置 一般不建议改变全局设置
  pyenv shell <python版本> # shell 会话设置 只影响当前的shell会话
  
  pyenv shell --unset # 取消 shell 会话的设置
  pyenv local <python版本> # local 本地设置 只影响所在文件夹
  pyenv 的 global、local、shell 的优先级关系是：shell > local > global
  ```

##### Node.js

- ```
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