<center> <h1> How to compile Linux kernel ( change name of machine ) <br> </h1> </center> 

## Reference
* https://www.cyberciti.biz/tips/compiling-linux-kernel-26.html

## Download kernel
* find the kernel version `uname -r`
* [linux kernel archives](https://www.kernel.org)
* extract tar.xz file using `tar -xvf linux-***.tar.xz`
* cd to extracted linux-*** folder
* `cp  -v /boot/config-$(uname -r) .config`
* open Makefile
* setting EXTRAVERSION = -M1130400477
* setting CONFIG_SYSTEM_TRUSTED_KEYS from "debian/canonical-certs.pem" to ""
* setting CONFIG_SYSTEM_REVOCATION_KEYS from "debain/canonical-certs.pem" to ""

## Download compliers and other tools
* `sudo apt install build-essential libncruses-dev bison flex libssl-dev libelf-dev`
* open Makfile


## compile
* `make -j $(nproc)`
* `sudo make module`
* `sudo make install`
* `sudo update-initramfs -c -k {your kernel version}` {kernel version}=5.19.11-M113040047
* `sudo update-grub`
* `reboot`

## Result
![result](/img/compile_kernel/part1_result.png)
