---
layout: post
title: Burn windows USB in MacOS
category: DV
description: process record
---



diskutil list

sudo diskutil eraseDisk FAT32 'name' MBRFormat 'place(/dev/disk2)'

unetbootin

//FAT32 对文件大小有限制，如果 .ios 文件超过4GB，安装时可能出现错误。
