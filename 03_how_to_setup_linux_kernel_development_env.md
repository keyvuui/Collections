# How to setup a Linux kernel module development environment

This article describes how to setup a linux kernel development on your own machine and cloud server.

- [How to setup a Linux kernel module development environment](#how-to-setup-a-linux-kernel-module-development-environment)
  - [Requirements](#requirements)
  - [Example environment](#example-environment)
  - [Basic Step](#basic-step)
  - [Optional Step](#optional-step)
  - [Change log](#change-log)

## Requirements

1.  Debian 9.x or other linux machine with kernel version >= 4.x . (Virtual machine is ok)
2.  A `C` compiler such like gcc or clang
3.  A text editor.

## Example environment

-   Operating System: `Arch Linux`

-   GCC version: `8.3.0`
-   Editor: `Visual-studio-code-insider with remote development plugin`

## Basic Step

1.  Change source to `debian testing` to get latest version software.
2.  Update source index.

    ```shell
    $ sudo apt update
    ```

3.  Install linux headers. The headers is located in my case is  `/usr/src/linux-5.1.4.arch1/`. You can just check what's in your directory exactly. 

    ```shell
    $ sudo apt install linux-headers
    ```

4.  Now, you can start build your first kernel module. But if we need a better experience, you need config your `vscode`. See further.

## Optional Step

In this section, we will explore some settings of Editor or IDE which can make us feel better. 

-   VScode

    Add those three path in you `C/C++` extensions setting.

    ```shell
    "/usr/src/linux-5.1.4.arch1/include/",
    "/usr/src/linux-5.1.4.arch1/arch/x86/include/",
    "/usr/lib/modules/5.1.4-arch1-1-ARCH/build/include/uapi/"
    ```

    It will make sure the extensions can found symbols and give you correct completion. 

-   Youcompleteme

    (WIP)

-   Clion

    (WIP)

## Change log

-   _5-24-2019_ First upload. 
