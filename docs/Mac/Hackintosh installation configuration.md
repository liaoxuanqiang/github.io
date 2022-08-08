# Hackintosh 安装配置

Hackintosh installation configuration

------

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

