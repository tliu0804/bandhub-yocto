# bandhub-yocto
## Build
initialize the build environment
```
cd bandhub-yocto
. sources/poky/oe-init-build-env
```
Add meta after switch to build folder automatically
```
bitbake-layers add-layer  ../sources/meta-raspberrypi/
bitbake-layers add-layer  ../sources/meta-openembedded/
```
start build...enjoy coffee
```
bitbake core-image-base
```
Check image after build finish
```
ls tmp/deploy/images/raspberrypi4/core-image-base-raspberrypi4.wic.bz2
```
## Flash
Prepare sdcard, and make sure which device node for you sdcard with following command - compare plug and unplug
```
ls /dev/sd*
```
suppose your sdcard is /dev/sdd, flashing to sdcard...
```
bzcat tmp/deploy/images/raspberrypi4/core-image-base-raspberrypi4.wic.bz2  | sudo dd of=/dev/sdd
```
## Boot
1. Connect Micro HDMI to your monitor
2. Power on, and you see the log in your monitor
3. Log in as root without password
4. Enjoy your linux
