# USB Wi-Fi Installation on Ubuntu (Realtek 8812BU)

This is to introduce the installation of USB Wi-Fi drivers for Realtek 8812BU.


Requirements:
- Ubuntu 18.04/20.04


Download the driver package [here](https://github.com/fastoe/RTL8812BU), unzip and name the folder as RTL8812BU.
```
cd RTL8812BU
sudo apt update
sudo apt install -y dkms git bc
VER=$(sed -n 's/\PACKAGE_VERSION="\(.*\)"/\1/p' dkms.conf)
sudo rsync -rvhP ./ /usr/src/rtl88x2bu-${VER}
sudo dkms add -m rtl88x2bu -v ${VER}
sudo dkms build -m rtl88x2bu -v ${VER}
sudo dkms install -m rtl88x2bu -v ${VER}
sudo modprobe 88x2bu
sudo reboot
```

Note: Most people don't use "Monitor Mode", so no need to look at the "Monitor Mode" section on GitHub.


Reference: https://blog.csdn.net/qq_36305156/article/details/119479767
