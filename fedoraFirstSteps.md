Fedora First steps 
==================

This are the first steps after a fresh installation of Fedora linux
1. SSH Server
enable ssh server

To start the sshd daemon, type the following at a shell prompt:
systemctl start sshd.service


If you want the daemon to start automatically at the boot time, type:
systemctl enable sshd.service

2. Install remote desktop
sudo dnf install xrdp
systemctl enable xrdp.service
systemctl start xrdp.service
systemctl enable xrdp-sesman.service
systemctl start xrdp-sesman.service
firewall-cmd --permanent --add-port=3389/tcp

3. Update system

It is recommended before installing some software like virtualbox

dnf update

4. Change hostname (requires restart)
echo $HOSTNAME
hostnamectl set-hostname - -static “myhostname”

5. Install google
To add Google Repository run all the below command in your Linux Console, as root.

# vi /etc/yum.repos.d/google-chrome.repo
Add following lines:

[google-chrome]
name=google-chrome - \$basearch
baseurl=http://dl.google.com/linux/chrome/rpm/stable/\$basearch
enabled=1
gpgcheck=1
gpgkey=https://dl-ssl.google.com/linux/linux_signing_key.pub

dnf install google-chrome-stable

6. Install virtualbox


Update prerequisite

dnf install -y kernel-headers kernel-devel dkms gcc

Add VirtualBox repos
cd /etc/yum.repos.d/
wget http://download.virtualbox.org/virtualbox/rpm/fedora/virtualbox.repo

dnf -y install VirtualBox-5.0
