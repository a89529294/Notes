changes linux to boot into graphical or text mode

```bash
sudo sytemctl get-default 

sudo systemctl set-default multi-user.target # or graphical.target
```