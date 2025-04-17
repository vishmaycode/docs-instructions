# Wifi Drivers


### Installing wifi drivers for my hp pavalion after every kernal update

### connect to wired network

### disable secure boot first use any password its temprary just remember till rebooting
```shell
sudo mokutil --disable-validation
reboot
```

### download the drivers and make install
```shell
git clone git://github.com/lwfinger/rtw89.git
cd rtw89/
make
sudo make install
```

### reboot and confirm the wifi is working
```shell
reboot
```

### enable secure boot
```shell
sudo mokutil --enable-validation
reboot
```
