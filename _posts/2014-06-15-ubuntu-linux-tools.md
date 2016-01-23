---
layout: page
date: 2014-06-15
title: Ubuntu, Linux - cmds, utils etc.
categories: tech
---

## Finding the current version of ubuntu
- uname -mrs
- lsb_release -a
- cat /etc/issue

## How to upgrade to latest ubuntu

* sudo apt-get update
* sudo apt-get upgrade
* sudo apt-get dist-upgrade

Then begin the upgrade process


* sudo apt-get install update-manager-core
* sudo do-release-upgrade
    - sudo do-release-upgrade -d (if **No new release found** msg pops up)

* <http://www.cyberciti.biz/faq/howto-upgrade-to-ubuntu-14-04-from-ubuntu-13-10-or-12-04>
* <http://lawrit.lawr.ucdavis.edu/it-help-center/how-to/upgrading-ubuntu-via-command-line>

## Switching terminals

* Ctrl + Alt + F1....F7
    - F7 - desktop

## Hibernating, Suspend system

* sudo pm-suspend
* sudo pm-hibernate

## Details for processor

* cat /proc/cpuinfo 

## Battery Charge details

* acpi

## Listing all attached drives

* sudo fdisk -l

## Making bootable usb stick

* <http://superuser.com/questions/591234/creating-a-bootable-usb-from-command-line-on-linux>
* <http://askubuntu.com/questions/372607/how-to-create-a-bootable-ubuntu-usb-flash-drive-from-terminal>

## Commands

* man -k <search item>
* id, groups, useradd, userdel, groupadd, groupdel
* /etc/passwd, /etc/group, 
* usermod - modify user accounts
* history, tail, head
* ./bash_profile
* alias
* env, set, export, $HOME, $SHELL, 

## network tools
* host <domain.com> for ip address
* nslookup <domain.com>
* dig <domain.com>
* ifconfig <interface> up/down
* ip addr show
* ip route show
* route -n (to show route table)
* traceroute <domain.com>
* nc -v -z hostname 80-1000 2>&1 /to scan ports (80 to 100) on hostname
* nc -k -l 4000 //to listen for connections on port 400
* nc hostname 4000 //to connect to hostname on port 
* netstat -(all(a), tcp(t), udp(u), listen(l), process(p), userid(e)) //e.g nestat -atp (all tcp with process name)


## command line utils

* cat, tac, Ctrl+D
* sed s/pattern/replace-patter/g <file> 
* awk -F: ‘{print $0..$6}’ file , -F: => use ‘:’ as field seperator
* sort file
* uniq file => uniq consecutive line entries in a file
* paste file1 file2 
* grep [pattern] file
* tr ‘from’ ‘trom’ < file
* ls -l | tee file.txt => prints to stdout and also to file.txt
* wc => word count
* less, head, tail
* du -sh * | sort -n (for list directories and their sizes in human readable format)


## bash utils/hacks
* alias
    - 'alias' just for listing existing alias
    - setting up alias -> alias = 'cd /usr; ls; cd -'
        use semicolon to seperate mutiliple commands
    - 'unalias' to reverse the association


## I/O redirection

* ls -l /usr > abcd.txt (stdout to abcd.txt)
* ls -l /usr >> abcd.txt (append stdout to abcd.txt)
* ls -l /usr 2> error.txt (stderror to error.txt)
* ls -l /usr &> out.txt (stdout and stderror to out.txt)
* ls -l /bin/usr 2> /dev/null (disposing std error)
* cat < lazy_dog.txt (changing stdinput for cat to contents of lazy_dog.txt)

## Listing directory sizes

* ncdu
