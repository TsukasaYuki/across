# Some useful scripts

l2tp.sh
=======

- Description: Auto install L2TP VPN for CentOS6+/Debian7+/Ubuntu12+
- Intro: https://teddysun.com/448.html
```bash
Usage: l2tp [-l,--list|-a,--add|-d,--del|-m,--mod|-h,--help]

| Bash Command     | Description                  |
|------------------|------------------------------|
| l2tp -l,--list   | List all users               |
| l2tp -a,--add    | Add a user                   |
| l2tp -d,--del    | Delete a user                |
| l2tp -m,--mod    | Modify a user password       |
| l2tp -h,--help   | Print this help information  |
```

bbr.sh
======

- Description: Auto install latest kernel for TCP BBR
- Intro: https://teddysun.com/489.html

LINODE的KVM架構LINUX更換內核 
文章转载自：Madlax的杂物房（http://madlax.pw/）
http://madlax.pw/2016/12/03/103.html


安裝Grub
安裝過程中可能會詢問安裝位置，不需要安裝到MBR

Arch Linux

pacman -S linux grub


CentOS 7

yum install kernel grub2


Debian

apt-get install linux-image-amd64 grub2


Fedora 22

dnf install kernel-core grub2


Ubuntu

apt-get install linux-image-virtual grub2


配置Grub

編輯/etc/default/grub，修改以下項目：

GRUB_TIMEOUT=10

GRUB_CMDLINE_LINUX="console=ttyS0,19200n8"

GRUB_DISABLE_LINUX_UUID=true

GRUB_SERIAL_COMMAND="serial --speed=19200 --unit=0 --word=8 --parity=no --stop=1"

GRUB_TERMINAL=serial


更新bootloader，更新內核後需要再一次運行該命令來更新GRUB目錄，

預設為清單第一個內核啟動：


Arch Linux

grub-mkconfig -o /boot/grub/grub.cfg


Debian 8 & Ubuntu 15.04

update-grub


CentOS 7

mkdir /boot/grub

grub2-mkconfig -o /boot/grub/grub.cfg


Fedora 22 - Replace with the current kernel version

dracut /boot/initrd-4.0.5-300.fc22.x86_64.img 4.0.5-300.fc22.x86_64 

mkdir /boot/grub

grub2-mkconfig -o /boot/grub/grub.cfg


重啟到Grub2 模式


在LINODE面板選擇編輯你的設定檔

Click on Edit under the Configuration Profiles section



在Boot Settings選項的Kernel清單裡選擇GRUB 2

In the Boot Settings section, select GRUB 2 from the Kernel drop down menu


點Save Changes保存，重啟機子後就可以按通常方式更換發行版本內核了。

啟動中可能會出現以下錯誤，可以忽略。

error: file `/boot/grub/i386-pc/all_video.mod' not found.

Loading Linux linux ...

Loading initial ramdisk ...

Press any key to continue...



bench.sh
========

- Description: Auto test download & I/O speed script
- Intro: https://teddysun.com/444.html
```bash
Usage:

| Option   | Bash Command                    |
|----------|---------------------------------|
| 1        | wget -qO- bench.sh | bash       |
| 2        | curl -Lso- bench.sh | bash      |
| 3        | wget -qO- 86.re/bench.sh | bash |
| 4        | curl -so- 86.re/bench.sh | bash |
```

backup.sh
=========

- You must modify the config before run it
- Backup MySQL/MariaDB/Percona datebases, files and directories
- Backup file is encrypted with AES256-cbc with SHA1 message-digest (option)
- Auto transfer backup file to Google Drive (need install `gdrive` command) (option)
- Auto transfer backup file to FTP server (option)
- Auto delete Google Drive's or FTP server's remote file (option)
- Intro: https://teddysun.com/469.html

```bash
Install gdrive command step:

For x86_64: 
wget -O /usr/bin/gdrive http://dl.lamp.sh/files/gdrive-linux-x64
chmod +x /usr/bin/gdrive

For i386: 
wget -O /usr/bin/gdrive http://dl.lamp.sh/files/gdrive-linux-386
chmod +x /usr/bin/gdrive
```

ftp_upload.sh
=============

- You must modify the config before run it
- Upload file(s) to FTP server
- Intro: https://teddysun.com/484.html

unixbench.sh
============

- Description: Auto install unixbench and test script
- Intro: https://teddysun.com/245.html

pptp.sh(Deprecated)
===================

- Description: Auto Install PPTP for CentOS 6
- Intro: https://teddysun.com/134.html

Copyright (C) 2013-2017 Teddysun <i@teddysun.com>
