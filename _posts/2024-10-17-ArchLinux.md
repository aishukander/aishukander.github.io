---
title: ArchLinux
date: 2024-10-17 14:06 +0800
categories: [教學]
tags: [Linux, ArchLinux, 系統, KDE, Plasma]
description: 安裝ArchLinux系統。
---

# 製作隨身碟
## 下載iso檔
先到[ArchLinux](https://archlinux.org/download/)官網下載iso檔。 <br>
下載時可以選擇使用磁力連結或直接下載，直接下載的話可以選擇日本的載點，距離比較近（作者人在台灣）。 <br>

![Desktop View](/assets/img/2024-10-17-ArchLinux/Worldwide.png)

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

![Desktop View](/assets/img/2024-10-17-ArchLinux/Locales.png)

## Disk configuration
Disk Configuration可以設定硬碟分割，沒特別需求的話可以依照教學直接使用一整顆硬碟。 <br>

![Desktop View](/assets/img/2024-10-17-ArchLinux/Disk1.png)

![Desktop View](/assets/img/2024-10-17-ArchLinux/Disk2.png)

![Desktop View](/assets/img/2024-10-17-ArchLinux/Disk3.png)

![Desktop View](/assets/img/2024-10-17-ArchLinux/Disk4.png)

完成後點擊<- Back就可以返回主畫面。 <br>

## BootLoader
選擇Grub(可以改的比較好看)。 <br>

## Hostname
就是電腦名稱，會顯示在路由器之類的地方。 <br>

## Root password
就是root帳號的密碼。 <br>

## User account
你的使用者帳號設定，建議主帳號在第二張圖那裡選擇yes。 <br>

![Desktop View](/assets/img/2024-10-17-ArchLinux/User1.png)

![Desktop View](/assets/img/2024-10-17-ArchLinux/User2.png)

![Desktop View](/assets/img/2024-10-17-ArchLinux/User3.png)

完成後點擊Confirm and exit就可以返回主畫面。 <br>

## Profile
如果要安裝Plasma作為電腦的桌面環境可以依照教學操作。 <br>

![Desktop View](/assets/img/2024-10-17-ArchLinux/Profile1.png)

![Desktop View](/assets/img/2024-10-17-ArchLinux/Profile2.png)

![Desktop View](/assets/img/2024-10-17-ArchLinux/Profile3.png)

## Audio
建議選擇Pipewire，Pipewire較新功能也較完全(像是支援aptx協定之類的)。 <br>

![Desktop View](/assets/img/2024-10-17-ArchLinux/Pipewire.png)

## Additional packagers
輸入noto-fonts-cjk去安裝支援中文的字型(不然進Plasma會出現一堆方框)，Enter後系統會自動尋找noto-fonts-cjk並在系統開始安裝時一併安裝。 <br>

![Desktop View](/assets/img/2024-10-17-ArchLinux/AdditionalPackagers.png)

## Network configuration
如果有要使用Plasma的話記得選Use NetworkManager。 <br>

![Desktop View](/assets/img/2024-10-17-ArchLinux/NetworkManager.png)

## Timezone
選擇你所在地的時區就好 <br>

## 開始安裝
全部選項完成後點擊Install進行安裝，第一下Enter會顯示你的安裝配置，第二次Enter後會倒數5秒，接下來就等電腦安裝完成。 <br>
安裝完成後會彈出以下畫面， <span style="font-weight: bold; font-size: 1.2em;">記得選NO</span> ，不然重開機後不會進到Plasma內。 <br>

![Desktop View](/assets/img/2024-10-17-ArchLinux/LastStep.png)

# 小問題
## Signature is unknown trust
如果太久沒更新ArchLinux就有可能這樣。 <br>
```bash
sudo pacman -Syu && pacman-key --refresh-keys 
```

## Unable to lock database
因為db.lck鎖定了pacman的數據庫，所以解法就是直接把db.lck刪了。 <br>
```bash
sudo rm /var/lib/pacman/db.lck
```

# 結尾
剛安裝好系統進到Plasma時你一定會想說怎麼那麼醜，此時就是進設定調設定的快樂時間了，但那是之後文章的部分了。 <br>
如果還是不知道怎麼裝ArchLinux的話可以去試試看[Endeavouros](https://endeavouros.com/)，Endeavouros簡單來說就是有GUI安裝介面的ArchLinux而已。 <br>
