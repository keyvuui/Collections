# How to setup llvm in MacOS

## Index

-   [How to setup llvm in MacOS][1]
    -   [Contents][2]
    -   [Why don't use Apple clang toolchain but llvm?][3]
    -   [How to install llvm][4]
        -   [Download the pre-compiled binary][5]
        -   [Build from source][6]
        -   [Install llvm from homebrew][7]
    -   [How to config llvm][8]
        -   [Config your environment variables][9]

## Why don't use Apple clang toolchain but llvm?

Apple clang is very new and don't need any pre-config. You can just use it when you run `xcode-select install`. But sometime it will not the latest version. You can't use some new added feature include clangd or new c++17 headers. So you may be want to use the llvm from [the LLVM project website][10].

## How to install llvm

**There is three way to install llvm.**

### Download the pre-compiled binary

Download pre-compiled binary from llvm project website. Then put them to your $PATH.
**I don't recommend this way.**

### Build from source

Clone the llvm repository. Follow the instruction from project, build from source.
**This maybe a little bit mess, but it still very simple.**

### Install llvm from homebrew

Use homebrew install llvm toolchain. You would better do it this way.
You just run one line code here:

```shell
$ brew install llvm
```

Coagulation! Here you go!

## How to config llvm

Once you done install llvm, you may be want to code something. But it wasn't the proper time. You may wonder why you can't compiled my cpp code. There are some errors such as "Can't found stdio.h" or missing some headers.

### Config your environment variables

You need to config it in your own shell profile. If you use bash you need to config `.bashrc`, else if you use zsh, you should edit your `.zshrc`.  Add blow line to your configuration file.

1.  Config `CFLAGS`, make complier can find your headers which in system. `CPATH` is the `include path` which compiler check it every time under compile process. Apple clang toolchain have a default include path, clang will use it when compile. But llvm's clang won't reference the default include path, so you should add it manually just like apple clang automatically do. 

    ```shell
    export CPATH=/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/lib/clang/10.0.0/include:/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/include:/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX10.14.sdk/usr/include:/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX10.14.sdk/System/Library/Frameworks
    ```

2.  Set `$PATH` so that shell can find clang or another tools.

    ```shell
    export PATH=/usr/local/opt/llvm/bin/:$PATH
    ```

[1]: #How-to-setup-llvm-in-MacOS

[2]: #Contents

[3]: #Why-dont-use-Apple-clang-toolchain-but-llvm

[4]: #How-to-install-llvm

[5]: #Download-the-pre-compiled-binary

[6]: #Build-from-source

[7]: #Install-llvm-from-homebrew

[8]: #How-to-config-llvm

[9]: #Config-your-environment-variables

[10]: https://llvm.org
