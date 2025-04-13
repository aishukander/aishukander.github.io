---
title: EnvyControl
date: 2024-10-01 12:35 +0800
categories: [教學]
tags: [Linux, ArchLinux, GPU, Nvidia, 驅動, 程式]
description: 在ArchLinux上使用EnvyControl來調整GPU模式
---

# 簡介
[EnvyControl](https://github.com/bayasdev/envycontrol)用於在Linux系統上切換GPU模式，可完全關閉獨顯來降低耗電跟發熱。 <br>
integrated為只開啟內顯的模式，nvidia為使用nvidia獨顯的模式，hybrid則是二者皆可調用的模式，需要使用獨顯時推薦使用hybrid模式加上Nvidia Prime來指定用nvidia獨顯執行程式。

# 安裝
## 基於[ArchLinux](https://archlinux.org/)的發行版的安裝方式(需要[yay](/posts/Yay))
```bash
yay -S envycontrol --noconfirm
```

# 切換方式
 <span style="font-weight: bold; font-size: 1.2em;">切換完成後記得重開機一下。</span> <br>

## 使用終端機切換
切換至混合 <br>
```bash
sudo envycontrol -s hybrid
```

切換至內顯 <br>
```bash
sudo envycontrol -s integrated
```

切換至獨顯 <br>
```bash
sudo envycontrol -s nvidia
```

查詢目前模式 <br>
```bash
envycontrol --query
```

## 使用[Optimus GPU Switcher](https://github.com/enielrodriguez/optimus-gpu-switcher)於plasma上切換
## 從AUR安裝[Optimus GPU Switcher](https://github.com/enielrodriguez/optimus-gpu-switcher)(需要[yay](/posts/Yay))
```bash
yay -S plasma6-applets-optimus-gpu-switcher-git --noconfirm
```

## 從[Discove](https://apps.kde.org/zh-tw/discover/)安裝
啟動Discove後 > Plasma Addons > Plasma Widgets 然後找到Optimus GPU Switcher for KDE 6。 <br>

## Optimus GPU Switcher的切換方式
工具列右下角應該會出現代表GPU廠家的符號

![Desktop View](/assets/img/2024-10-01-EnvyControl/SystemTrayIcon.png)

進入選單後依照需求選擇對應模式即可

![Desktop View](/assets/img/2024-10-01-EnvyControl/ToggleButton.png)
