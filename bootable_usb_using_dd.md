### checking the lable of pendrive

 - plug usb
```shell
sudo fdisk -l
```

### formating pendrive
```shell
sudo umount /dev/sdb
sudo mkfs.vfat /dev/sdb -I
```
 - unplug and plug

### making it bootable

```shell
sudo umount /dev/sdb
sudo dd bs=4M if=/Downloads/linux_mint_20.iso of=/dev/sdb status=progress && sync
```
