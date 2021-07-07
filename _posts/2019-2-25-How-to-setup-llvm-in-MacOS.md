# How to setup llvm in MacOS

- [How to setup llvm in MacOS](#how-to-setup-llvm-in-macos)
  - [What difference between Apple clang and llvm's clang?](#what-difference-between-apple-clang-and-llvms-clang)
  - [How to install llvm](#how-to-install-llvm)
    - [Use homebrew](#use-homebrew)
  - [How to config llvm](#how-to-config-llvm)
    - [Config your environment variables](#config-your-environment-variables)

## What difference between Apple clang and llvm's clang?

Apple clang is bundled with command line tool and `Xcode`. It have almost every feature if compare it to LLVM clang, but it lacks some extra tools for example `clang-format` and `clangd`. If you need them, you should install `LLVM`. Additionally, if you want to use unstable feature from compiler such as `C++20` features, you may need `LLVM`.

## How to install llvm

I only recommend install `LLVM` by using homebrew.

### Use homebrew

Use homebrew install llvm toolchain. You would better do it this way.
You just run one line code here:

```shell
    $ brew install llvm
```

If you want the latest version, you can build it from source.

```shell

    $ brew install llvm --HEAD
```

## How to config llvm

Once you have llvm installed, you need to set some environment variables to make `LLVM` work.

### Config your environment variables

1.  You don't need to set all kind of environment variables, just use `xcrun` to set that automatically. Make sure use all llvm relate command with xcrun:

    ```shell
    $ xcrun clang foo.c
    ```

2.  Set `$PATH` so that shell can find clang or another tools.

    ```shell
    export PATH=/usr/local/opt/llvm/bin/:$PATH
    ```
