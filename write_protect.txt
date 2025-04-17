
# Fix readonly drive

```shell
sudo hdparm -r0 /dev/sdb1
```

### read only pendrive
[https://askubuntu.com/questions/826425/cannot-copy-to-usb-every-usb-stick-is-read-only-16-04](https://askubuntu.com/questions/826425/cannot-copy-to-usb-every-usb-stick-is-read-only-16-04)

```shell
df -Th
find /dev/sda1 -type f -exec chmod 666 {} \;
```
or 
```shell
find /dev/sda1 -type f -exec chmod 644 {} \;
```
