---
title: OrcaSlicer
date: 2024-12-26 23:40 +0800
categories: [教學]
tags: [ArchLinux, Flatpak, Slicer]
description: 安裝OrcaSlicer來對模型切片
---
# 安裝
## Archlinux安裝
因為從AUR下載來編譯太耗時了，所以使用[anarsoul](https://github.com/anarsoul)的Flatpak版本。 <br>
從GitHub下載最新發行版並安裝。 <br>
```bash
cd ~/Downloads

latest_release=$(curl -s https://api.github.com/repos/anarsoul/io.github.softfever.OrcaSlicer/releases/latest | jq -r .tag_name)
download_url=$(curl -s https://api.github.com/repos/anarsoul/io.github.softfever.OrcaSlicer/releases/latest | jq -r '.assets[] | select(.name | endswith(".flatpak")) | .browser_download_url')
wget "$download_url" -O "io.github.softfever.OrcaSlicer_$latest_release.flatpak"

flatpak install --user "./io.github.softfever.OrcaSlicer_$latest_release.flatpak" -y

rm "./io.github.softfever.OrcaSlicer_$latest_release.flatpak"
```

加入環境變數以避免OrcaSlicer出現顯示問題。 <br>
```bash
flatpak override OrcaSlicer --env=__EGL_VENDOR_LIBRARY_FILENAMES=/usr/lib/x86_64-linux-gnu/GL/default/share/glvnd/egl_vendor.d/50_mesa.json
flatpak override OrcaSlicer --env=WEBKIT_DISABLE_COMPOSITING_MODE=1
```
