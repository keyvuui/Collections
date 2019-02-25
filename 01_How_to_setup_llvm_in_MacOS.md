# How to setup llvm in MacOS

[TOC]

## Why don't use Apple clang toolchains but llvm?
Apple clang is very new and don't need any preconfig. You can just use it when you run `xcode-select install`. But sometime it will not the latest version. You can't use some new added feature include clangd or new c++17 headers. So you may be want to use the llvm from [the LLVM project website](https://llvm.org).

## How to install llvm

**There is three way to install llvm.**

### Download the pre-compiled binary
Download pre-compiled binary from llvm project website. Then put them to your $PATH. 
**I don't recommend this way.**

### Build from source
Clone the llvm repo. Follow the instruction from project, build from source.
**This maybe a little bit mess, but it still very simple.**

### Install llvm from homebrew
Use homebrew install llvm toolchains. You would better do it this way.
You just run one line code here:
```shell
$ brew install llvm
```
Congulation! Here you go!

## How to config llvm 
Once you done install llvm, you may be want to code something. But it wasn't the proper time. You may wonder why you can't compiled my cpp code. There are some errors such as "Can't found stdio.h" or missing some headers. 

### Config your enveriment variables

You need to config it in your own shell profile. If you use bash you need to config `.bashrc`, else if you use zsh, you should edit your `.zshrc`.  Add blow line to your configuration file.

1. Config `CFLAGS`, make complier can find your headers which in system.

   ```shell
   export CPATH=/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/lib/clang/10.0.0/include:/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/include:/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX10.14.sdk/usr/include:/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX10.14.sdk/System/Library/Frameworks 
   ```

2. Set `$PATH` so that shell can find clang or another tools.

   ```shell
   export PATH=/usr/local/opt/llvm/bin/:$PATH
   ```

## Config youcompleteme(optional)

If you use vim, you probable use youcompleteme. To use youcompleteme you need to add headers directory to your `.ycm_extra_conf.py`, such as: 

```python
flags = [
    '-Wall',
    '-Wextra',
    '-Werror',
    '-fexceptions',
    '-DNDEBUG',
    '-std=c++11',
    '-x',
    'c++',
    '-isystem',
    '/usr/include',
    '-isystem',
    '/usr/local/include',
    '-isystem',
    '/usr/local/opt/llvm/include/c++/v1/',
    '-isystem',
    '/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX.sdk/usr/include/'
]
```