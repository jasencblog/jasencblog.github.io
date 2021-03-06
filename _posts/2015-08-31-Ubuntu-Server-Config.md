---
layout: post
title:  "Ubuntu Server Config"
date:   2015-08-31
---

I'm using [VirtualBox](https://www.virtualbox.org/) and accessing it with [Vagrant](https://www.vagrantup.com/).

## Getting Started  

To create a new virtual machine using Vagrant, from the working directory `$ vagrant init ubuntu/trusty64`. Trusty64 represents Ubuntu Server 14.04.3 LTS. Run `$ vagrant up`, the first time this is run the virtual machine will be downloaded. `$ vagrant ssh`, cool we're in Ubuntu.

Note: You may want to forward a port from your host machine to your virtual machine. Open up your Vagrantfile and uncomment `# config.vm.network "forwarded_port", guest: 80, host: 8080` so you can access a localhost:8080.

### Update Ubuntu

* `$ sudo apt-get update` - Download and update all of our packages.
* `$ sudo apt-get upgrade` - Install all of those new packages.

Combine them with `&&` to start getting fancy.

## Ubuntu Secruity

Vagrant does us a favor here and disables `root` user SSH while creating a new user named `vagrant` with `sudo` powers and SSH login. Let's do it manually anyway.

* `$ sudo adduser username`, provide a password and any optional additional information.
* `$ sudo nano /etc/sudoers.d/username` and add `username ALL=(ALL) NOPASSWD:ALL`, write out and exit.
* If you'd like to connect to that new user through Vagrant `$ ssh username@127.0.0.1 -p 2222`.

If you need to disable `root` SSH manually follow this [How-To-Geek article](http://www.howtogeek.com/howto/linux/security-tip-disable-root-ssh-login-on-linux/) and check the comments for additional security ideas.

### Key Based Authentication

Still need to add SSH to the new username. Generate private keys on local machine only, generating on server risks privacy.

* `$ ssh-keygen`
* `/Users/Username/.ssh/filename` and add passphrase
* `$ cat .ssh/filename.pub` and copy output. Note: Make sure you copy the `.pub`
file, otherwise you're going to copy the private key and that is no bueno.

Place the .pub file on the server. After connecting through with the new username:

* `$ mkdir .ssh && nano .ssh/authorized_keys`
* Paste contents of .pub file, write out and exit.
* `$ chmod 700 .ssh`
* `$ chmod 644 .ssh/authorized_keys`

[`chmod`](https://en.wikipedia.org/wiki/Chmod) and [File System Permission](https://en.wikipedia.org/wiki/File_system_permissions).

Log out of username. Log back in using SSH:

* `$ ssh username@127.0.0.1 -p 2222 -i ~/.ssh/filename`
* One time dialog prompt asking for SSH passphrase.

### Disable Password Logins

Increase security by only allowing SSH key pair logins. From the server logged in through username via SSH:

* `$ sudo nano /etc/ssh/sshd_config` Note: Same file for preventing root SSH.
* Find this line `PasswordAuthentication yes`
* Edit it to `PasswordAuthentication no`, write out and exit.
* `$ sudo service ssh restart` to restart the service.

### Firewalls

Ubuntu has a firewall preinstalled, make sure it is inactive by `$ sudo ufw status`. Then:

* `$ sudo ufw default deny incoming`
* `$ sudo ufw default allow outgoing`
* `$ sudo ufw allow ssh` and if using Vagrant `$ sudo ufw allow 2222/tcp`
* `$ sudo ufw allow www`
* `$ sudo ufw enable` say yes

Note: if you're now locked out, nuke your server and start again.
