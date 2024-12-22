---
title: DockerWindows
date: 2024-11-23 13:53 +0800
categories: [教學]
tags: [ArchLinux, Windows, Docker, 虛擬化]
description: 在Docker裡運行Windows
---

# 安裝和使用
## 安裝Docker、Docker-Compose、usbutils
```bash
sudo pacman -Syu
sudo pacman -S docker docker-compose usbutils
```

## 安裝Remmina
```bash
flatpak install flathub org.remmina.Remmina
```

## 用usbutils找到要給Windows的USB口
先使用usbutils查看未插入USB裝置的狀態 <br>
```bash
lsusb -t
```

插上USB裝置後再使用一次usbutils來找到有變化的部分。 <br>

![Desktop View](/assets/img/2024-11-23-DockerWindows/usbutils.png)

從圖片中我們可以知道該USB口的bus為2，port為1。 <br>

## 開始寫Compose
到你想放Windows的地方創一個資料夾，進到裡面並開啟終端機。 <br>
```bash
mkdir storage
mkdir data
nano Docker-Windows.yml
```

貼上整個yml檔。 <br>
詳細配置方法可以在[dockur/windows](https://github.com/dockur/windows)的GitHub找到。 <br>
```yml
services:
  windows:
    image: dockurr/windows
    container_name: windows
    environment:
      VERSION: "<你要的Windows版本>"
      GPU: "Y"
      USERNAME: "<Windows的使用者名>"
      PASSWORD: "<Windows的密碼>"
      DISK_SIZE: "<分配的硬碟大小>"
      RAM_SIZE: "<分配的記憶體大小>"
      CPU_CORES: "<分配的CPU核心數>"
      ARGUMENTS: "-device usb-host,hostbus=<用usbutils找到的bus>,hostport=<用usbutils找到的port>"
    devices:
      - /dev/kvm
      - /dev/dri
      - /dev/bus/usb
      - /dev/net/tun
    volumes:
      - <資料夾路徑>/storage:/storage
      - <資料夾路徑>/data:/data
    cap_add:
      - NET_ADMIN
    ports:
      - 3389:3389/tcp
      - 3389:3389/udp
    stop_grace_period: 2m
```

## 啟動Windows
先用一般模式確定運作正常。 <br>
```bash
docker compose -f Docker-Windows.yml up
```

等待出現 <span style="font-weight: bold; font-size: 1.2em;">localhost:8086</span> 確定沒問題後Ctrl+C關閉compose。 <br>
加入-d參數來讓compose在後台掛起。 <br>
```bash
docker compose -f Docker-Windows.yml up -d
```

## 如果要卸除Docker-Windows的Compose
對容器的配置更改時都需要先卸除該容器的Compose。 <br>
```bash
docker compose -f Docker-Windows.yml down
```

## 用Remmina連接Windows
進入Remmina後點擊左上角的加號。 <br>

![Desktop View](/assets/img/2024-11-23-DockerWindows/Remmina.png)

選擇RDP後把該填的填好後點Save就好。 <br>
之後就可以從Remmina的主畫面快速連接Windows了。 <br>

## Remmina的暗色主題
右上角設定按鈕 > Preferences > Appearance > 把Prefer dark thems打勾 <br>

![Desktop View](/assets/img/2024-11-23-DockerWindows/RemminaPreferences.png)

![Desktop View](/assets/img/2024-11-23-DockerWindows/RemminaDarkThems.png)
