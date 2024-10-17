---
title: ArchLinux
date: 2024-10-17 14:06 +0800
categories: [教學]
tags: [Linux, 系統]
description: 安裝ArchLinux系統。
---

# 製作隨身碟
## 下載iso檔
先到[ArchLinux](https://archlinux.org/download/)官網下載iso檔。 <br>
下載時可以選擇使用磁力連結或直接下載，直接下載的話可以選擇日本的載點，距離比較近（作者人在台灣）。 <br>

![Desktop View](/assets/img/2024-10-17-ArchLinux/ArchLinuxWorldwide.png)

下載完成後可用SHA256驗證檔案正確性(在Checksums and signatures下面一些的位置)。 <br>

## 將iso檔放入Ventoy
接下來依照之前[Ventoy](/posts/Ventoy)的文章將開機隨身碟製作好。 <br>

# 使用archinstall安裝系統
把隨身碟插上電腦後讓電腦從隨身碟啟動，並選擇ArchLinux後開機。 <br>
開機完成後輸入以下指令。 <br>
```bash
archinstall
```

進去後會看到以下畫面。 <br>

![Desktop View](/assets/img/2024-10-17-ArchLinux/ArchInstallMainScreen.png)

## Locales
Locales內的可以設定鍵盤、系統語言、編碼類型。 <br>

![Desktop View](/assets/img/2024-10-17-ArchLinux/ArchLinuxLocales.png)

## Disk configuration
Disk Configuration可以設定硬碟分割，沒特別需求的話可以依照教學直接使用一整顆硬碟。 <br>

![Desktop View](/assets/img/2024-10-17-ArchLinux/ArchLinuxDisk1.png)

![Desktop View](/assets/img/2024-10-17-ArchLinux/ArchLinuxDisk2.png)

![Desktop View](/assets/img/2024-10-17-ArchLinux/ArchLinuxDisk3.png)

![Desktop View](/assets/img/2024-10-17-ArchLinux/ArchLinuxDisk4.png)

完成後點擊<- Back就可以返回主畫面。 <br>

## BootLoader
選擇Grub(可以改的比較好看)。 <br>

## Hostname
就是電腦名稱，會顯示在路由器之類的地方。 <br>

## Root password
就是root帳號的密碼。 <br>

## User account
你的使用者帳號設定，建議主帳號在第二張圖那裡選擇yes。 <br>

![Desktop View](/assets/img/2024-10-17-ArchLinux/ArchLinuxUser1.png)

![Desktop View](/assets/img/2024-10-17-ArchLinux/ArchLinuxUser2.png)

![Desktop View](/assets/img/2024-10-17-ArchLinux/ArchLinuxUser3.png)

## Profile
如果要安裝Plasma作為電腦的桌面環境可以依照教學操作。 <br>

# 未完後補
