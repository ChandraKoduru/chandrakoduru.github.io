---
title: Booting ubuntu into console mode
date: 2014-06-17
layout: post
tags: [ubuntu, tech]
categories: tech
---


### Original Post

<http://ubuntuhandbook.org/index.php/2014/01/boot-into-text-console-ubuntu-linux-14-04>

### How to

1. sudo vim /etc/default/grub

2. Make the following changes
    * Comment the line GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”
    * Change GRUB_CMDLINE_LINUX=”” to GRUB_CMDLINE_LINUX=”text”
    * Uncomment this line #GRUB_TERMINAL=console
    * Should look like below
    * ![this](/assets/Ubuntu-text-mode.png)

3. sudo update-grub
