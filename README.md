[![Linux/OS X build status](https://img.shields.io/travis/seahug/parconc-examples/master.svg?label=Linux%2FOS%20X)](https://travis-ci.org/seahug/parconc-examples)
[![Windows build status](https://img.shields.io/appveyor/ci/mgsloan/parconc-examples/master.svg?label=Windows)](https://ci.appveyor.com/project/mgsloan/parconc-examples/branch/master)

# SeaHUG "Parallel and concurrent programming in Haskell" materials

## About the book

To get more information about the source text "Parallel and Concurrent
Programming in Haskell" by Simon Marlow, please visit the [book's web
site][book]. You can purchase the book or read it online there for free.

## Installing stack

Stack is a tool for downloading, installing, and building haskell projects.  It
takes care of handling multiple compiler versions, and supports sandboxing
sharing build results between projects.

### Windows 64bit

Download and run the installer from
[here](https://www.stackage.org/stack/windows-x86_64-installer).

Also, take a look at the instructions
[here](http://docs.haskellstack.org/en/stable/install_and_upgrade/#windows).
While not strictly necessary, it is a good idea to use `set
STACK_ROOT=c:\stack_root` with stack, due to windows MAX_PATH restrictions.

### Mac OS

```
brew install haskell-stack
```

### Linux 64bit

There are also distribution specific versions (see the "Other" section below),
but I find this to be the most straightforward way to get a recent version:

```
wget https://github.com/commercialhaskell/stack/releases/download/v1.0.4/stack-1.0.4-linux-x86_64.tar.gz
mkdir -p ~/.local/bin
tar -xvf stack-1.0.4-linux-x86_64.tar.gz
mv stack-1.0.4-linux-x86_64/stack ~/.local/bin/stack

# Optionally, remove the archive and its unpacked dir
rm -r stack-1.0.4-linux-x86_64
rm stack-1.0.4-linux-x86_64.tar.gz
```

Then, try `which stack`. If the response is not the `.local/bin/stack` folder
within your home directory, then you will need to add `.local/bin/stack` to your
PATH. To do this, add the following to your `~/.profile`, and then start a new
terminal:

```
if [ -d "$HOME/.local/bin" ] ; then
    PATH="$HOME/.local/bin:$PATH"
fi
```

### Other

See the installation instructions
[here](http://docs.haskellstack.org/en/stable/install_and_upgrade/).

## Cloning this repo and setting up your environment

Clone this repo as follows:

```
git clone https://github.com/seahug/parconc-examples.git
```

We then ask stack to set up an appropriate version of GHC:

```
cd pcph/
stack setup
```

## Loading examples into ghci

Usually we'll only want to load up a single example at a time.  `stack ghci` is
a good way to do this:

```
mgsloan@computer:~/oss/seahug/pcph$ stack ghci --no-build :parmonad
There were multiple candidates for the Cabal entry "Lex" (/home/mgsloan/oss/seahug/pcph/examples/parinfer/Lex.x), picking /home/mgsloan/oss/seahug/pcph/examples/parinfer/Lex.hs
There were multiple candidates for the Cabal entry "Parse" (/home/mgsloan/oss/seahug/pcph/examples/parinfer/Parse.y), picking /home/mgsloan/oss/seahug/pcph/examples/parinfer/Parse.hs
There were multiple candidates for the Cabal entry "Lex" (/home/mgsloan/oss/seahug/pcph/examples/parinfer/Lex.x), picking /home/mgsloan/oss/seahug/pcph/examples/parinfer/Lex.hs
There were multiple candidates for the Cabal entry "Parse" (/home/mgsloan/oss/seahug/pcph/examples/parinfer/Parse.y), picking /home/mgsloan/oss/seahug/pcph/examples/parinfer/Parse.hs
The following GHC options are incompatible with GHCi and have not been passed to it: -threaded
Using main module: 1. Package `parconc-examples' component exe:parmonad with main-is file: /home/mgsloan/oss/seahug/pcph/examples/parmonad.hs
Configuring GHCi with the following packages: parconc-examples
GHCi, version 7.8.4: http://www.haskell.org/ghc/  :? for help
Loading package ghc-prim ... linking ... done.
Loading package integer-gmp ... linking ... done.
Loading package base ... linking ... done.
Loading package array-0.5.0.0 ... linking ... done.
Loading package deepseq-1.3.0.2 ... linking ... done.
Loading package containers-0.5.5.1 ... linking ... done.
Loading package old-locale-1.0.0.6 ... linking ... done.
Loading package time-1.4.2 ... linking ... done.
Loading package random-1.0.1.1 ... linking ... done.
Loading package abstract-deque-0.3 ... linking ... done.
Loading package abstract-par-0.3.3 ... linking ... done.
Loading package bytestring-0.10.4.0 ... linking ... done.
Loading package cereal-0.4.1.1 ... linking ... done.
Loading package transformers-0.3.0.0 ... linking ... done.
Loading package mtl-2.1.3.1 ... linking ... done.
Loading package monad-par-extras-0.3.3 ... linking ... done.
Loading package primitive-0.6.1.0 ... linking ... done.
Loading package vector-0.10.12.3 ... linking ... done.
Loading package mwc-random-0.13.4.0 ... linking ... done.
Loading package parallel-3.2.0.6 ... linking ... done.
Loading package monad-par-0.3.4.7 ... linking ... done.
unknown option: 'c'
[1 of 1] Compiling Main             ( /home/mgsloan/oss/seahug/pcph/examples/parmonad.hs, interpreted )
Ok, modules loaded: Main.
*Main> :set args 4 5
*Main> main
13
*Main> :t fib
fib :: Integer -> Integer
*Main> :bro
fib :: Integer -> Integer
main :: IO ()
```

## Building all examples

To build optimized versions of the examples, run `stack build`.  Then, you can
run the example by name by using `stack exec`.  For example, `stack exec --
parmonad 4 5`.

# License

Released under MIT License

[book]: http://chimera.labs.oreilly.com/books/1230000000929
[cabal-install]: https://wiki.haskell.org/Cabal-Install
[docker-install]: https://docs.docker.com/engine/installation/
[docker]: https://www.docker.com/
[ghc]: https://www.haskell.org/downloads
[gnu-make]: https://www.gnu.org/software/make/
[haskell-docker]: https://hub.docker.com/_/haskell/
[network-windows]: http://neilmitchell.blogspot.com/2010/12/installing-haskell-network-library-on.html
[official]: http://chimera.labs.oreilly.com/books/1230000000929/ch01.html#sec_sample
