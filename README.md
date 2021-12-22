# Intro
op7仓库是由活跃于XDA论坛的blu spark发布，适用于OnePlus7/7T/7TPro设备。

blu_spark-10分支，适用于Android 10的设备。

OnePlus在github官方也开源了内核代码，blu spark基于此开发，添加了一些feature。

为何选择使用blu spark, 而不选用OnePlus官方的内核代码库？
根据经验，使用OnePlus官方发布的内核代码编译生成的内核，刷入设备后会遇到WIFI失效等问题。blu spark的op7仓库则不会遇到此问题。

这里基于blu spark的op7做了一点修改，以支持内核功能开发。

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
