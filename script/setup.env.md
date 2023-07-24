# Setup Env

## Ubuntu 20.04.03

From "user guide - svet branch", 
## 1.2.1 "Upgrade to LTS for 11th Gen Tiger Lake processor"

```
sudo apt install coreutils build-essential bc kmod cpio flex
libncurses5-dev libelf-dev libssl-dev bison
wget https://github.com/intel/linux-intellts/archive/refs/tags/lts-v5.10.90-yocto-220208T044440Z.zip
unzip lts-v5.10.90-yocto-220208T044440Z.zip
cd linux-intel-lts-lts-v5.10.90-yocto-220208T044440Z
make olddefconfig #Select the default value for unset config
items
make -j8
sudo -E make INSTALL_MOD_STRIP=1 modules_install
sudo -E make install
```

```
wget https://github.com/intel/intel-linuxfirmware/raw/main/tgl_guc_65.4.0.bin
wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linuxfirmware.git/plain/i915/tgl_huc_7.9.3.bin
wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linuxfirmware.git/plain/i915/tgl_dmc_ver2_12.bin
sudo cp *.bin /lib/firmware/i915
sudo update-initramfs -u -k all
```


```
sudo vi /etc/default/grub

GRUB_CMDLINUX_LINUX_DEFAULT='quiet splash i915.force_probe=* i915.enable_guc=2"
GRUB_CMDLINUX_LINUX=""

sudo -E update-grub
```


```
uname -a
sudo cat /sys/kernel/debug/driv/0/i915_gpu_info | grep firmware
```


## NEO

### 1.2.5
```
mkdir neo; cd neo
wget https://github.com/intel/intel-graphicscompiler/releases/download/igc-1.0.11222/intel-igccore_1.0.11222_amd64.deb
wget https://github.com/intel/intel-graphicscompiler/releases/download/igc-1.0.11222/intel-igcopencl_1.0.11222_amd64.deb
wget https://github.com/intel/computeruntime/releases/download/22.20.23198/intel-level-zero-gpudbgsym_1.3.23198_amd64.ddeb
wget https://github.com/intel/computeruntime/releases/download/22.20.23198/intel-level-zerogpu_1.3.23198_amd64.deb
wget https://github.com/intel/computeruntime/releases/download/22.20.23198/intel-opencl-icddbgsym_22.20.23198_amd64.ddeb
wget https://github.com/intel/computeruntime/releases/download/22.20.23198/intel-openclicd_22.20.23198_amd64.deb
wget https://github.com/intel/computeruntime/releases/download/22.20.23198/libigdgmm12_22.1.2_amd64.
deb
sudo dpkg -i *.deb
```


```
sudo usermod -a -G video USER
sudo usermod -a -G render USER
```


### 1.2.6
```
su
cd /opt/intel/openvino_2022/extras/scripts/
wget
https://storage.openvinotoolkit.org/repositories/openvino/packa
ges/2022.1/opencv/openvino_opencv_ubuntu20.tgz
mv openvino_opencv_ubuntu20.tgz ../../
cd ../../
tar zxvf openvino_opencv_ubuntu20.tgz
```