---
title: OrcaSlicer
date: 2024-12-04 14:10 +0800
categories: [教學]
tags: [Linux, 程式, Slicer]
description: 在Linux上安裝OrcaSlicer
---

# 安裝
## Flatpak版
Flatpak版還沒有被官方支援，但有人做好放到GitHub了。 <br>
先到[GitHub](https://github.com/anarsoul/io.github.softfever.OrcaSlicer/releases)上下載最新版並安裝。 <br>
```bash
cd ~/Downloads
flatpak install <下載到的檔名>.flatpak 
```

# 處理問題
## Setup或Prepare頁面無畫面
```bash
cd ~/Desktop
nano io.github.softfever.OrcaSlicer.desktop
```

找到Exec那行並在開頭加上這段環境變數。 <br>
```text
__EGL_VENDOR_LIBRARY_FILENAMES=/usr/share/glvnd/egl_vendor.d/50_mesa.json WEBKIT_DISABLE_COMPOSITING_MODE=1
```

## Switching language failed
到locale.gen內把en_GB.UTF-8 UTF-8取消注釋
```bash
sudo nano /etc/locale.gen
```

完成後重新生成locale
```bash
sudo locale-gen
```

## 沒有黑暗模式
建立主題資料夾並複製Breeze-Dark，然後開啟Flatpak對該資料夾的讀取權限，再設定Flatpak程式使用的主題。 <br>
```bash
mkdir ~/.themes
cp -r /usr/share/themes/Breeze-Dark ~/.themes
sudo flatpak override --filesystem=~/.themes
sudo flatpak override --env=GTK_THEME=Breeze-Dark
```
