Mutt
====

Custom compilation using Mac Port
----------------------------------

sudo port install -f mutt-devel +ssl+headercache+smtp+sasl

The command compiles mutt with the compilation parameter `ssl` `headercache` `smpt` and `sasl`

Why are the parameters required?

For example, smtp is not compiled by default. When the parameter is not provided then smtp options cannot be used in the mutt config because mutt was not compiled to support smpt.

How to know the compilation parameter of mutt when it is already installed?
---------------------------------------------------------------------------

mutt -v


