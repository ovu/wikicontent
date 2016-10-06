Compile vim with clipboard support
==================================

The steps shown below are inspired in the following blog entry:
http://gustavepate.github.io/blog/20131010/compiling-vim-enable-python-system-copy-paste/

Install dependencies
=====================

In the article are installed several dependencies however in Linux fedora I just needed to install some of them:
-libgnome-devel
-libXt-devel
-libX11-devel


Fetch vim sources
=================

git clone https://github.com/vim/vim

Clean previous builds
=====================

If you already compiled vim it is necessary to clean it:
cd vim/src
make distclean
cd ..


Configure vim
=============

sudo ./configure --enable-pythoninterp=yes \
                 --enable-rubyinterp=yes \
                 --with-features=huge \
                 --enable-gui=auto \
                 --enable-gnome-check  \
                 --enable-gtk2-check \
                 --with-x \
                 --enable-multibyte

Install vim
============

Execute the following commands:

make
sudo make install


The previous steps were used to build and install Vim 8 with ruby, python and clipboard support in Fedora.

My machine had already python and ruby installed.
