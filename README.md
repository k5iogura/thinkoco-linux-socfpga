# thinkoko-linux-socfpga

### Why backup?  
[[original git is here]](https://github.com/thinkoco/linux-socfpga)  
I cannot found linux-socfpga 3.10.x tag anywhere. Linux-ltsi release was expired and erased.  
But I need 3.10.x version for of linux source code to rebuild linux kernel for DE10Nano(Cortex-A9) to support UVC Camera with OpenCL feature.

features bellow,
1. Backup for Linux source code using in DE10Nano OpenCL-BSP .
2. Linux Version is socfpga 3.18.0-00266-g9a879ba.
3. Supporting UVC Camera and execution of OpenCL kernel without installing HDMI-Hardware IP on FPGA Fabric.

## Testing

0. opkg ready.
1. About darknet framework, darknet_ttt for TTT5_224_160.cfg.
2. About UVC Camera by cheese.
3. About Internet access through HostPC(Windows7/CentOS7).

![](https://raw.githubusercontent.com/thinkoco/c5soc_opencl/master/picture/arch.png)

## How to build zImage and socfpga.dtb on HostPC(Linux)
  
$ git clone https://github.com/k5iogura/thinkoco-linux-socfpga.git  
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
