# Openvpn issue

### Fix using nmconnection file

 - Add the VPN connection as normal using the Network Manager GUI
 - Edit the connection file in /etc/NetworkManager/system-connections/(connectionname).nmconnection where (connectionname) is the name of your VPN conection
```shell
sudov /etc/NetworkManager/system-connections/connectionname.nmconnection
sudo nano /etc/NetworkManager/system-connections/connectionname.nmconnection
```
 - In the [vpn] section, beneath the line that starts ca=, add a new line reading
 - tls-cipher=DEFAULT:@SECLEVEL=[0-5] here 0-5 is the range, use the below line for pasting
```shell
tls-cipher=DEFAULT:@SECLEVEL=0
```
 - Save the file
```shell
sudo systemctl restart NetworkManager
```
 - Start the VPN connection as normal and it should connect, make sure you dont edit connection via GUI, if you do then repeat the steps as the connection file will be overwritten.


# fix using default gateway
One more solutions was to change default gateway order
```shell
route add default gw {IP-ADDRESS} {INTERFACE-NAME}
route add default gw 192.168.1.254 eth0
```

