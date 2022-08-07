# WSL命令
WSL command

------

## WSL 基本命令

```
wsl --install #安装 WSL 和 Linux 的 Ubuntu 发行版
wsl --install -d <Distribution Name> #安装特定的 Linux 发行版
wsl --list --online #列出可用的 Linux 发行版
wsl --list --verbose #列出已安装的 Linux 发行版
wsl --set-version <distribution name> <versionNumber> #将 WSL 版本设置为 1 或 2
wsl --set-default-version <Version> #设置默认 WSL 版本
wsl --set-default <Distribution Name> #设置默认 Linux 发行版
wsl ~ #将目录更改为主页
wsl --distribution <Distribution Name> --user <User Name> #通过 PowerShell 或 CMD 运行特定的 Linux 发行版
wsl --update #更新 WSL
wsl --status #检查 WSL 状态
wsl --help #Help 命令
wsl -u <Username>`, `wsl --user <Username> #以特定用户的身份运行
<DistributionName> config --default-user <Username> #更改发行版的默认用户
wsl --shutdown #关闭
wsl --unregister <DistributionName> #注销或卸载 Linux 发行版
wsl --mount <DiskPath> #装载磁盘或设备
```

## 在 WSL 上运行Linux GUI应用

```
sudo apt update #更新发行版中的包
sudo apt install gedit -y #安装 Gedit，若要在编辑器中启动 bashrc 文件，请输入：gedit ~/.bashrc
sudo apt install gimp -y #安装 GIMP，若要启动，请输入：gimp
sudo apt install nautilus -y #安装 Nautilus，若要启动，请输入：nautilus
sudo apt install vlc -y #安装 VLC，若要启动，请输入：vlc
sudo apt install x11-apps -y #安装 X11 应用，若要启动，请输入要使用的工具的名称。 例如：xcalc, xclock, xeyes
```

## 在 WSL 上安装Google Chrome

```
cd /tmp #将目录更改为 temp 文件夹
sudo wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb #使用 wget 下载Google Chrome
sudo dpkg -i google-chrome-stable_current_amd64.deb #获取当前稳定版本
sudo apt install --fix-broken -y #修复包
sudo dpkg -i google-chrome-stable_current_amd64.deb #配置包
```

若要启动，请输入：google-chrome

## 在 WSL 上安装Microsoft Teams

```
cd /tmp #将目录更改为 temp 文件夹
sudo curl -L -o "./teams.deb" "https://teams.microsoft.com/downloads/desktopurl?env=production&plat=linux&arch=x64&download=true&linuxArchiveType=deb" #使用 curl 下载包
sudo apt install ./teams.deb -y #使用 apt 安装Microsoft Teams
```

若要启动，请输入：teams

## 在 WSL 上安装Microsoft Edge浏览器

## 在 WSL 上安装 Node.js

```
sudo apt-get install curl #安装 cURL（用于在命令行中从 Internet 下载内容的工具）
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash #安装 nvm
command -v nvm #验证安装
nvm ls #列出当前安装的 Node 版本
nvm install --lts #安装 Node.js 的当前稳定的 LTS 版本
nvm install node #安装 Node.js 的当前版本
nvm ls #列出安装的 Node 版本
node --version #验证 Node.js 是否已安装，以及是否为当前默认版本
npm --version #验证是否也有 npm
```