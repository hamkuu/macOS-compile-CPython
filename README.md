# How to Compile CPython on macOS

## Pre-requisites

- macOS 14.2 (23C64)
- [Homebrew](https://brew.sh)

## Install dependencies

Minimum

```bash
brew install openssl zlib
```

Nice to have

```bash
brew install xz gdbm sqlite
```

## Configure `zlib` package path for compilers to locate

```bash
export LDFLAGS="-L/opt/homebrew/opt/zlib/lib"
export CPPFLAGS="-I/opt/homebrew/opt/zlib/include"
```

## Clone CPython source code

```bash
git clone git@github.com:python/cpython.git -b 3.12
git clean -fdx
```

## Generate a Makefile

```bash
cd cpython
./configure --with-openssl="$(brew --prefix openssl@3.0)" --enable-optimizations
```

## Build CPython binary

```bash
make -j2 -s
```

## Test Python

```bash
make test
```

## Install Python

```bash
# Install a standalone version (e.g. python3.11) and won't create symbolic link for python3
sudo make altinstall

# Create symbolic link for python3
sudo make install
```
