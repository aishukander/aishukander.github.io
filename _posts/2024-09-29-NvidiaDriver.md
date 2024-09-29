---
title: Nvidia驅動
date: 2024-09-29 12:56 +0800
categories: [教學]
tags: [Linux, 程式, 驅動, GPU]
description: 在ArchLinux上安裝nvidia驅動
---

# 安裝
## DKMS版驅動安裝
DKMS版的驅動會在核心更新時自動編譯。 <br>
```bash
sudo pacman -Syyu
sudo pacman -S nvidia-dkms nvidia-utils linux-headers
```

<span style="font-weight: bold; font-size: 1.2em;">重開機後</span> 使用lspci來確定驅動安裝完成。 <br>

```bash
sudo lspci -k | grep -A 2 -i "NVIDIA"
```

出現 *Kernel driver in use: nvidia* 代表驅動安裝成功。
![Desktop View](/assets/img/2024-09-29-Nvidia/lspci.png){: width="972" height="589" }

## nvtop安裝
如果想要查看顯卡使用率可以安裝該程式。
```bash
sudo pacman -S nvtop
```

安裝完成後可於終端機輸入 *nvtop* 來啟動該程式。
![Desktop View](/assets/img/2024-09-29-Nvidia/nvtop.png){: width="972" height="589" }
_按下ctrl+c即可退出nvtop_
