# LLVM development trouble shooting

- [LLVM development trouble shooting](#llvm-development-trouble-shooting)
  - [Build `Kaleidoscope` chapter 2 code failed.](#build-kaleidoscope-chapter-2-code-failed)
    - [Description](#description)
    - [Step](#step)


## Build `Kaleidoscope` chapter 2 code failed.

### Description
When try to build code from `Kaleidoscope` chapter 2, got an error: 

![llvm::DisableABIBreakingChecks](img/09/llvm::DisableABIBreakingChecks.png)

It's cause by missing some link library. Simply we can just add the link option to our build command. In this case, it is `--ldflags --system-libs --libs core`. If you use `-v` paramater to see what actually happen when link time and compare it with the failed one, you will see what different. 

![link_comparsion](img/09/link_comparison.png)

The second command link some LLVM stuff more than first one, and the `llvm::DisableABIBreakingChecks` is contains in `LLVMSupport`.


### Step
1. Make sure you are using a new compiler which support `c++14` standard at least.
2. Install latest LLVM toolchain in you local machine.
3. Use this command instead of the website one.
    ```shell
    $ clang++ -v -g -O3 toy.cpp `llvm-config --cxxflags --ldflags --system-libs --libs core`
    ```
4. Test program by running `./a.out`.
