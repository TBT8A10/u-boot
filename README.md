### Information
Building an old revision of Rockchip's U-Boot, I was able to obtain a binary very similar to the stock one.
Currently, it boots Android without any visible issues.

### Build process
* Download [Linaro 6.3.1 toolchain](https://releases.linaro.org/components/toolchain/binaries/6.3-2017.05/aarch64-linux-gnu/gcc-linaro-6.3.1-2017.05-x86_64_aarch64-linux-gnu.tar.xz)
* `make rk3368_defconfig`
* `make CROSS_COMPILE=<toolchain-path>/bin/aarch64-linux-gnu- -j$(nproc --all)`
* Unpack stock `uboot.img` with imgRePackerRK
* Replace `uboot.bin` with the one you just built
* Repack `uboot.img` with imgRePackerRK
* Flash on your device