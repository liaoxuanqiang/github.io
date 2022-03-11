# Windows11 使用管理

## 系统安装

1.查询最新版 Windows11 系统信息

```
https://changewindows.org/timeline
```
2.下载[Windows11](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewiso)安装镜像

3.下载[EasyU](https://www.itsk.com/forum.php?mod=viewthread&tid=422456)制作PE启动盘

4.电脑插入U盘进入PE系统，利用磁盘工具对磁盘进行分区，之后安装系统

## 系统优化

1.电源管理启动卓越性能模式
```powershell
powercfg -duplicatescheme e9a42b02-d5df-448d-aa00-03f14749eb61
```
2.关闭休眠
```powershell
powercfg -h off
```
3.关闭 VBS
```powershell
bcdedit /set hypervisorlaunchtype off
bcdedit /set hypervisorlaunchtype auto
```
4.关闭虚拟内存

5.修改组策略(gpedit.msc)禁用宽带预留
