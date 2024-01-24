# BTT CB1 Customization

## pi user alias fro biqu
Create the `pi` user and give him the same ID as biqu (1000)
```bash
useradd -o -u 1000 -g 1000 pi
# user usermod instead of useradd if pi already exists
```
this makes ssh pi@host go to /home/biqu

basically pi = biqu

## create script and guide compatibility
created a bind mount from `/home/biqu` to `/home/pi` which then looks and works like real data

add to the `/etc/fstab` with `nano` or `vim` & reboot
```bash
/home/biqu /home/pi none defaults,bind 0 0
```


## disable Wifi checker

see https://github.com/bigtreetech/CB1-Kernel/issues/10

> in this file, the script tries to constantly connect to a wifi network, by default this is set to a test network which doesn't exist, causing lagging and other issues specially in KlipperScreen.


create a back and then add a `break` before the sleep to break out of the endless loop
```bash
cp /boot/scripts/connect_wifi.sh /boot/scripts/connect_wifi.sh.bak
sed -i '/sleep $check_interval/i \ \ \ \ \ \ \ \ break' /boot/scripts/connect_wifi.sh
```



