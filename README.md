### Information
Building an old revision of Rockchip's U-Boot, I was able to obtain a binary very similar to the stock one. However, Incar made modifications to the code (e.g. on the LCD driver) to make it compatible with the tablet. \
Currently, this U-Boot loads Android without any issues. Initially the LCD didn't work but with some changes now it does. However, as of now there's an issue which makes the screen not turn on again after turning it off.

### Build process
* Download [Linaro 6.3.1 toolchain](https://releases.linaro.org/components/toolchain/binaries/6.3-2017.05/aarch64-linux-gnu/gcc-linaro-6.3.1-2017.05-x86_64_aarch64-linux-gnu.tar.xz)
* `make rk3368_defconfig`
* `make CROSS_COMPILE=<toolchain-path>/bin/aarch64-linux-gnu- -j$(nproc --all)`
* Unpack stock `uboot.img` with imgRePackerRK
* Replace `uboot.bin` with the one you just built
* Repack `uboot.img` with imgRePackerRK
* Flash on your device