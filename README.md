### Information
Building an old revision of Rockchip's U-Boot, I was able to obtain a binary very similar to the stock one.

### Modifications
* Logs are printed on the LCD
* Removed read limit on LOADER mode
* Fastboot mode can be entered by pressing volume down
* Offline charging is now done in U-Boot instead of Android, this is useful because GSIs don't support offline charging.
    * U-Boot charging also has the advantage of showing battery percentage and information about the charging current & voltage.
* New fastboot commands:
    * `oem rockusb`: Reboots into LOADER (rockusb) mode

### Known issues
* The LCD may not turn on as some tablets may come with different LCDs. If that's the case, let me know

### Hotkeys
* With the tablet OFF:
    * With USB disconnected:
        * `Enter Recovery:` Power + Volume Up
        * `Enter Fastboot:` Power + Volume Down
    * With USB connected:
        * `Enter LOADER mode:` Volume Up
        * `Enter Fastboot:` Volume Down

### Build process
* Download [Linaro 6.3.1 toolchain](https://releases.linaro.org/components/toolchain/binaries/6.3-2017.05/aarch64-linux-gnu/gcc-linaro-6.3.1-2017.05-x86_64_aarch64-linux-gnu.tar.xz)
* `make rk3368_defconfig`
* `make CROSS_COMPILE=<toolchain-path>/bin/aarch64-linux-gnu- -j$(nproc --all)`
* Unpack stock `uboot.img` with imgRePackerRK
* Replace `uboot.bin` with the one you just built
* Repack `uboot.img` with imgRePackerRK
* Flash on your device