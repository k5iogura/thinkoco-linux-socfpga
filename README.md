# thinkoko-linux-socfpga

1. Backup for Linux source code using in DE10Nano OpenCL-BSP [original here](https://github.com/thinkoco/linux-socfpga).
2. Linux Version is socfpga 3.18.0-00266-g9a879ba.
3. supporting UVC Camera, OpenCL kernel.
4. not supporting HDMI-IP.

## testing

0. opkg ready.
1. darknet_ttt for TTT5_224_160.cfg OK!.
2. UVC Camera by cheese by opkg OK!.
3. Internet access through HostPC(Windows7/CentOS7) OK!

![](https://raw.githubusercontent.com/thinkoco/c5soc_opencl/master/picture/arch.png)

## Build zImage and socfpga.dtb on HostPC(Linux)
  
$ git clone https://github.com/thinkoco/linux-socfpga.git  
$ cd linux-socfpga  
$ git checkout -b socfpga-opencl_3.18 origin/socfpga-3.18  
$ cp config_opencl .config  
$ export ARCH=arm  
$ export CROSS_COMPILE=arm-linux-gnueabihf-  
$ export LOADADDR=0x8000  
  
$ make zImage  
$ make socfpga_cyclone5_de10_nano.dtb  
$ make modules_install INSTALL_MOD_PATH=~/sdcard/  
  
$ cp ~/sdcard/linux-socfpga/arch/arm/boot/zImage ./  
$ cp ~/sdcard/linux-socfpga/arch/arm/boot/dts/socfpga_cyclone5_de10_nano.dtb  ./socfpga.dtb  
