# Intro

适用于Android 10的op7仓库分支。
基于blu spark的op7做了一点修改，以支持内核功能开发。

# Build
在Ubuntu 18.04上使用的交叉编译工具链是[gcc-arm-10.2](https://developer.arm.com/-/media/Files/downloads/gnu-a/10.2-2020.11/binrel/gcc-arm-10.2-2020.11-x86_64-aarch64-none-linux-gnu.tar.xz?revision=972019b5-912f-4ae6-864a-f61f570e2e7e&hash=69DCE959E8C9BCB04BC33D907D537CBD30ED56E9)
在armDeveloper网站可以找到其他版本的gcc，但适用于本分支内核编译的是gcc-arm-10.2。（blu spark在[XDA帖子](https://forum.xda-developers.com/t/kernel-blu_spark-r106-op7-pro-oos-custom-a10.3944179/)里说使用的是`Build with custom toolchain blu_gcc-10.1`, 网上找不到）

```

# Assume cross_toolchain contains the gcc-arm-10.2
export CROSS_COMPILE=cross_toolchain/gcc-arm-10.2-2020.11-x86_64-aarch64-none-linux-gnu/bin/aarch64-none-linux-gnu-
export ARCH=arm64
export SUBARCH=arm64
export ANDROID_AARCH64=cross_toolchain/gcc-arm-10.2-2020.11-x86_64-aarch64-none-linux-gnu/bin
export PATH=$PATH:$ANDROID_AARCH64

# then
cd op7
make O=out blu_spark_defconfig
make O=out -j4
```
