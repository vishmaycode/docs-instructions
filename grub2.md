# Grub configs for silent boot

Open the file in any cli editor

```shell
sudo nvim /etc/default/grub
sudo nano /etc/default/grub
```

### Ubuntu
```shell
GRUB_DEFAULT=0
GRUB_TIMEOUT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_DISTRIBUTOR=`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash loglevel=3 vt.handoff=7"
GRUB_CMDLINE_LINUX="quiet splash"
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_RECORDFAIL_TIMEOUT=0
GRUB_FORCE_HIDDEN_MENU=true
#GRUB_DISABLE_OS_PROBER=true
```

### Debian 12
```shell
GRUB_DEFAULT=0
GRUB_TIMEOUT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_DISTRIBUTOR=lsb_release -i -s 2> /dev/null || echo Debian
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash loglevel=3 vt.handoff=7"
GRUB_CMDLINE_LINUX="quiet splash"
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_RECORDFAIL_TIMEOUT=0
GRUB_TERMINAL=console
```

Update the grub config
```shell
sudo update-grub
```


## Playmouth themes

Link to theme : [https://www.gnome-look.org/p/1360336](https://www.gnome-look.org/p/1360336)

```shell
sudo apt install plymouth plymouth-themes
sudo cp -r theme-folder /usr/share/plymouth/themes/
```

create if not exist
```shell
sudo nano /etc/initramfs-tools/conf.d/splash
```

and add this contents
```shell
FRAMEBUFFER=y
```

then run below commands to update
```shell
sudo plymouth-set-default-theme -R your-theme
sudo update-initramfs -u
```
