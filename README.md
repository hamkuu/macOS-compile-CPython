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
