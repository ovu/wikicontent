Virtualbox install or update in fedora
======================================

I was running virtualbox for a while in fedora and updated it several times successfully.
However after one update I got the following error in virtualbox saying I should execute the following command:

sudo /sbin/vboxconfig


After executing the command I was getting the following message:

vboxdrv.sh: Starting VirtualBox services.
vboxdrv.sh: Building VirtualBox kernel modules.
This system is not currently set up to build kernel modules (system extensions).
Running the following commands should set the system up correctly:

  yum install kernel-core-devel-4.6.4-301.fc24.x86_64
(The last command may fail if your system is not fully updated.)
  yum install kernel-core-devel
vboxdrv.sh: failed: Look at /var/log/vbox-install.log to find out what went wrong.
This system is not currently set up to build kernel modules (system extensions).
Running the following commands should set the system up correctly:

  yum install kernel-core-devel-4.6.4-301.fc24.x86_64
(The last command may fail if your system is not fully updated.)
  yum install kernel-core-devel

There were problems setting up VirtualBox.  To re-start the set-up process, run
  /sbin/vboxconfig
as root.


# Analysis on the message

After trying several things I realized that the version of the install rpm of kernel-devel was not the same as in the expected version in the previous messages.

The second observation was that executing the following command:

uname -r

was giving another version of the kernel.

So I realized the install rpm package kernel-devel and my kernel version were not the same. How did it happen? It is something I still don't know. I guess I upgraded my kernel in the past.

# Solution

I was trying to install kernel-devel with the correct version using some solutions found here:

http://stackoverflow.com/questions/33200717/vagrant-up-and-vm-doesnt-work-fedora-22

Basically the solution was to uninstall kernel-devel and install the one with the correct version:

sudo dnf install kernel-devel-$(uname -r)

however it did not work because it could not find the package.

I found the solution in the following link, where it describes how to install virtualbox in fedora 22, 23 or 24.

http://www.if-not-true-then-false.com/2010/install-virtualbox-with-yum-on-fedora-centos-red-hat-rhel/

The solution was to update the packages of the system running the following command:

sudo dnf update

Then compare the kernel version of the rmp package and the current used in the system.

rpm -qa kernel |sort -V |tail -n 1
 
uname -r

They were different version and it was necessary to reboot the system.

Then I could install the package and I got the correct version. The one the matched with uname -r

sudo install kernel-devel

Then I run the command:

sudo /sbin/vboxconfig

And it run without errors.

