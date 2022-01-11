[◀️ Go Back to README](https://github.com/psudo-dev/42cursus_04_born2beroot/)

### Table of Content   <!-- omit in toc -->

- [Mandatory](#mandatory)
  - [LVM Setup](#lvm-setup)
  - [Sudo](#sudo)
  - [UFW](#ufw)
  - [SSH](#ssh)
  - [Password policy](#password-policy)
  - [Scheduling a script](#scheduling-a-script)
  - [Monitoring script](#monitoring-script)
- [Bonus](#bonus)
  - [WordPress](#wordpress)
  - [FTP](#ftp)

---

### Basic Commands

```bash
# update and upgrade packages
sudo -- sh -c "apt update && apt upgrade"

# check if package was installed
dpkg -l | grep <package>

# change hostname
sudo hostnamectl set-hostname <hostname>
```

[<div align="right">back to top ⇧</div>](#table-of-contents)

---

## Mandatory

### LVM Setup

For [more information](https://www.youtube.com/watch?v=GEl2S5MI-WU)

### Sudo

- Install `sudo`
- `TTY` enabled (Teletype Mode)

```bash
# enter super user mode
su -

# create a user
sudo adduser <username>

# create a group and add a user to a group
sudo addgroup <groupname>
sudo adduser <username> <groupname>

# what users are part of a group
getent group <groupname>

# check if password was created
getent passwd <username>

# what groups a user belongs
groups <username>
```

```bash
# sudo rules
/etc/sudoers.d/<filename>

# sudo log
/var/log/sudo/<filename>
```

### UFW

```bash
# enable UFW
sudo ufw enable

# status
sudo ufw status

# allow/deny a port
sudo ufw allow <port>
sudo ufw deny <port>

# delete a rule
sudo ufw status numbered
sudo ufw delete <port position>

```

### SSH

```bash
# SSH status
sudo service ssh status

# connect to a remote SSH machine through a specific port
ssh <username>@<hostname> -p <port>

# SSH configuration
/etc/ssh/sshd_config
```

### Password policy

Install `libpam-pwquality`

```bash
# password expiration info
sudo chage -l <username>

# for password policy
/etc/login.defs
/etc/pam.d/common-password
/etc/security/pwquality.conf
```

### Scheduling a script

Use `cron`

```bash
# edit cron jobs
sudo crontab [-u <username>] -e

# list cron jobs
sudo crontab [-u <username>] -l
```

### Monitoring script

```bash
# commands
awk
grep
sed
uniq
wc
printf

# system info
uname

# CPU info file
/proc/cpuinfo

# RAM info
free

# Drive info
df

# CPU usage
iostat

# boot info
who

# LVM info
lsblk

# connections
ss

# IP
ip
curl -s ifconfig.me
hostname -I

# login info
journalctl

# date
WEEK=$(date +"%A")
DAY=$(date +"%d")
MONTH=$(date +"%b")
YEAR=$(date +"%Y")
TIME=$(date +"%R")
TZ_ALPHA=$(date +"%Z")
TZ_NUM=$(date +"%:z")
```

[<div align="right">back to top ⇧</div>](#table-of-contents)

---

## Bonus

### WordPress

Install

- `lighttpd`
- `mariadb-server`
- `wget`
- `php-cgi`
- `php-mysql`

> Remember to change folder and files' ownership and permissions if necessary

```bash
# configure
sudo lighty-enable-mod fastcgi
sudo lighty-enable-mod fastcgi-php

# reload service
sudo service lighttpd force-reload

# html connections
sudo ufw allow 80

# download and extract wordpress
sudo wget http://wordpress.org/latest.tar.gz (-P <PATH>)
sudo tar -xzvf <file> (-C <PATH>)

# wordpress folder
/var/www/html
```

### FTP

Install `vsftpd`

for [more information](https://www.digitalocean.com/community/tutorials/how-to-set-up-vsftpd-for-a-user-s-directory-on-debian-10)

```bash
# access FTP
ftp <ip-address>

# restart FTP
sudo service vsftpd restart

# ports
# FTP
21
20
# TLS
990
# passive ports
40000-50000

# ftp directory
/home/<username>/ftp

# vsftpd configuration
/etc/vsftpd.conf
/etc/vsftpd.userlistv
```

[◀️ Go Back to README](https://github.com/psudo-dev/42cursus_04_born2beroot/)