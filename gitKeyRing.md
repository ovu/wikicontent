Configure gnome keyring in linux fedora
=======================================

Based on the blog https://marklodato.github.io/

$ sudo apt-get install libgnome-keyring-dev
$ cd /usr/share/doc/git/contrib/credential/gnome-keyring
$ sudo make
$ sudo rm git-credential-gnome-keyring.o
$ sudo mv git-credential-gnome-keyring /usr/bin
$ git config --global credential.helper gnome-keyring

Restart the machine! Before it I was getting the error: Error communicating with gnome-keyring-daemon
