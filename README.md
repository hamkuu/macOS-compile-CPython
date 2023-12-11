# How to Compile CPython on macOS

## Get `brew` package manager from `brew.sh`

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

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
git clone git@github.com:python/cpython.git -b 3.11
```

## Generate a Makefile

```bash
cd cpython
./configure --with-openssl=$(brew --prefix openssl) --enable-optimizations
```

## Build CPython binary

```bash
make -j2 -s
```

## Install Python

```bash
# Install a standalone version (e.g. python3.11) and won't create symbolic link for python3
sudo make altinstall

# Create symbolic link for python3
sudo make install
```
