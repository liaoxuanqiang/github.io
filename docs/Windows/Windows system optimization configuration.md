# Windows 系统优化配置 

Windows system optimization configuration

------

1.电源管理启动卓越性能模式
```powershell
powercfg -duplicatescheme e9a42b02-d5df-448d-aa00-03f14749eb61

powercfg /? #查看详细使用方法
Powercfg -s <GUID> #使用命令格式
Powercfg -l #获取<GUID>
Powercfg /q #显示当前活动方案的内容

电源方案 GUID:381b4222-f694-41f0-9685-ff5bb260df2e (平衡)
电源方案 GUID:8c5e7fda-e8bf-4a96-9a85-a6e23a8c635c (高性能) *
电源方案 GUID:a1841308-3541-4fab-bc81-f71556f20b4a (节能)
Power Scheme GUID: e9a42b02-d5df-448d-aa00-03f14749eb61  (Ultimate Performance)
eg:
Powercfg -s 8c5e7fda-e8bf-4a96-9a85-a6e23a8c635c #切换电源方案为高性能模式

注册表路径为\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Power\PowerSettings
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