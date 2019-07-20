# Archlinux troubleshooting guidance

This guidance contains the most common problem user may occurs in archlinux daily use.

## Table of content

- [Archlinux troubleshooting guidance](#Archlinux-troubleshooting-guidance)
  - [Table of content](#Table-of-content)
  - [`clang-format` failed by don't have some shared library(libtinfo.so.5)](#clang-format-failed-by-dont-have-some-shared-librarylibtinfoso5)
    - [Description](#Description)
    - [Step](#Step)

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
