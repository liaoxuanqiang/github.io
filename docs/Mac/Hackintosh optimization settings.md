# Hackintosh 优化设置

Hackintosh optimization settings

------



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

## 