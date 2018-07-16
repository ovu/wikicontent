GHC-mod Installation
====================

Errors during installation are because GHC-mod does not support the newest ghc.

https://stackoverflow.com/questions/50948485/stack-install-ghc-mod-fails-with-dependencies-conflicts-on-osx-10-13-4

Reinstall stack

  curl -sSL https://get.haskellstack.org/ | sh -s - -f

Install ghc-mod with the supported version of ghc

  stack install ghc-mod --resolver lts-8.24

