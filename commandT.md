Command-T
=========
Vim Plugin to search files. It is a C plugin that should be compiled with C.

Requirements:
* Ruby
* gvim should be compiled with the same ruby version of the system

How to verify the ruby version in gvim?
:puts RUBY_VERSION

Compilation parameters of gvim
------------------------------

Note: Before the installation verify which `arch` parameters were used to compile gvim. 

To find the arch parameters execute the following command:
  gvim --version | grep --color arch

To set the correct `arch` compiler parameters execute the following command:
  export ARCHFLAGS="-arch x86_64"

Installation
------------
In the directory
~/.vim/bundle/command-t/ruby/command-t
execute the following commands:
  sudo ruby extconf.rb
  sudo make

Troubleshooting
---------------
If something went wrong and you need to compile again Command-t, then clean first the files that were compiled before:
  git clean -xdf
