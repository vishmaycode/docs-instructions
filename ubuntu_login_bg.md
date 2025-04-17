# background for ubuntu desktop login screen

mybg.jpg
download img and move to /usr/share/backgrounds/


## old way of changing background
--------------------------------------------

```shell
sudo gedit /etc/alternatives/gdm3.css
```
and search for 
```shell
#lockDialogGroup{
	background: none;
	....
	..
}
```
change this to 

```shell
background: url(file:///usr/share/backgrounds/mybg.png);
background-repeat: no-repeat;
background-size: cover;
background-position: center;
```

DONE!! that it!
----------------------------------------------


## new way

#### download the essentials
```shell
sudo apt install wget libglib2.0-dev-bin
```
#### download 
```shell
wget github.com/thiggy01/change-gdm-background/raw/master/change-gdm-background
```

#### give execution permisisons
```shell
chmod +x change-gdm-background
```

#### copy file to user local bin so can be accessed from anywhere easily
```shell
sudo cp change-gdm-background /usr/local/bin
```

#### run
```shell
sudo change-gdm-background /usr/share/backgrounds/mybg.png
```
