# Archlinux troubleshooting guidance

This guidance contains the most common problem user may occurs in archlinux daily use.

## Index

- [Archlinux troubleshooting guidance](#archlinux-troubleshooting-guidance)
  - [Index](#index)
  - [`clang-format` failed by don't have some shared library(libtinfo.so.5)](#clang-format-failed-by-dont-have-some-shared-librarylibtinfoso5)
    - [Description](#description)
    - [Step](#step)
  - [Can't resize the window of an archlinux guest in `vmware fusion`](#cant-resize-the-window-of-an-archlinux-guest-in-vmware-fusion)
    - [Description](#description-1)
    - [Step](#step-1)

## `clang-format` failed by don't have some shared library(libtinfo.so.5)

### Description

When use clang-format to format a cpp file, you may occurs an error like `libtinfo.so.5: cannot open shared object file: No such file or directory` especially in `vscode`.
It's all about missing a shared library `libtinfo.so.5`. It is a symbol link to `libncursesw.so.6`. Just create it then everything ok.

### Step

1.  Check wether `libncursesw.so.6` exist.
    ```shell
    $ ls /usr/lib/libncursesw.so.6
    ```
2.  Create symbol link we need.
    ```shell
    $ ln -sf /usr/lib/libncursesw.so.6 /usr/lib/libtinfo.so.5
    ```
3.  Verify `clang-format` worked. Once it done, `clang-format` would work.
    ```shell
    $ clang-format foo.cpp
    ```

## Can't resize the window of an archlinux guest in `vmware fusion`

### Description

When open a archlinux guest, I can't resize the window. Which means the screen won't autofill the whole window and resolution won't fit automatically.

It may cause by `open-vm-tools`, you need to exit `vmware fusion` completely and reopen it. Besides, when you use a desktop vm which use `wayland`, you may get the same experience.

### Step

1.  Check wether `open-vm-tool` installed.
2.  Exit `vmware fusion` and reopen it.
3.  Resize and check if work.
