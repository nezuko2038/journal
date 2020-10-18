---
layout: post
category: Linux
tags: [X]
revdate:  2019-03-28 00:00:00 +0900
---
# Linuxのグラフィックス関連



## DRMとは

* カーネルの機能
* Mesaが使用する

## DRIとは

* Direct Rendering Infrastructure
* DRMはDRIを実現するための実装

## フレームバッファとは
* Linux kernel 2.2 から本格的に使用できるようになった
* /dev/fb0や/dev/fb1のようなブロックデバイスでアクセスできる



フレームバッファデバイスの解説::
https://linuxjf.osdn.jp/JFdocs/kernel-docs-2.2/fb/framebuffer.txt.html
Linux Kernel 2.6 のフレームバッファ::
https://www.mztn.org/linux/k26fb.html


### 確認方法


```console
cd /usr/src/linux
make menuconfig
```

Qtライブラリが使用できる場合は、X上で、`make xconfig` でもいい。

## Xorg

### 設定ファイル

/etc/X11/xorg.conf.d ディレクトリー ::
ユーザー固有の設定

/etc/X11/xorg.conf::
/etc/X11/xorg.conf.dよりも優先される

### startx
Xを起動するためのスクリプト

### /etc/X11/xorg.conf

#### 生成


```
Xorg -configure
```

### ドライバ
#### xorg-x11-drv-dummy

* X.org dummy video driver
* ヘッドレスサーバには必要
* http://cosmolinux.no-ip.org/raconetlinux2/dummy_radeon_nvidia.html
* https://www.xpra.org/xorg.conf

#### xorg-x11-drv-void

* X.Org X11 void input driver
https://www.x.org/releases/X11R7.5/doc/man/man4/void.4.html

### xresprobe

ノート PC および DDC 準拠の画面に対して標準の解像度を調査し、 専用の形式で解釈しやすい出力を返すパッケージ


## VirtualGL
Requirement ::
https://cdn.rawgit.com/VirtualGL/virtualgl/2.6.1/doc/index.html#hd004001

## Xdummy

* https://xpra.org/trac/ticket/580#comment:3
* https://xpra.org/trac/wiki/Xdummy
* https://lists.freedesktop.org/archives/xorg/2017-April/058718.html
