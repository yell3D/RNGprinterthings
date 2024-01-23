# BTT CB1 Changes

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
