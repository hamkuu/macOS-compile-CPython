# How to Compile CPython on macOS

## Install dependencies

```bash
brew install openssl xz zlib gdbm sqlite
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
