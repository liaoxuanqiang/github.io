# 系统优化

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