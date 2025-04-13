---
title: Nvidia Prime
date: 2024-10-02 21:14 +0800
categories: [教學]
tags: [Linux, ArchLinux, GPU, Nvidia, 驅動, 程式]
description: 在ArchLinux上利用Nvidia Prime指定使用的GPU
---

# 簡介
Nvidia Prime是一種允許在Linux系統上使用混合GPU的技術，可在需要性能時使用獨顯、需要省電時使用內顯。 <br>

# 安裝
## 基於[ArchLinux](https://archlinux.org/)的發行版的安裝方式
```bash
sudo pacman -Syu --noconfirm
sudo pacman -S nvidia-prime --noconfirm
```

# 使用方法
如果有安裝[EnvyControl](/posts/EnvyControl)記得先將GPU模式更改為hybrid。 <br>

## 從終端機指定
假設要用獨顯啟動從AUR安裝的VSCode。 <br>
```bash
prime-run code
```

假設要用獨顯啟動從Flathub安裝的PrismLauncher。 <br>
```bash
prime-run flatpak run org.prismlauncher.PrismLauncher
```
## 在Plasma桌面的程式連結指定
在桌面找到要設定的程式的連結 > 右鍵 > 屬性 > 應用程式 > 在環境變數輸入該環境變數。 <br>
```text
__NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia __VK_LAYER_NV_optimus="NVIDIA_only"
```
![Desktop View](/assets/img/2024-10-02-NvidiaPrime/PlasmaEnv.png)

### 為Steam內特定遊戲指定
在Steam找到要設定的遊戲 > 右鍵 > 內容 > 在啟動參數輸入該參數 <br>
```text
__NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia __VK_LAYER_NV_optimus="NVIDIA_only" %command%
```

![Desktop View](/assets/img/2024-10-02-NvidiaPrime/SteamEnv.png)
