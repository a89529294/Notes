## _ip link_

The command `ip link` is used in Linux to display and manage network interfaces. When you run `ip link`, it shows the status of all network interfaces on your system, including whether they are **"UP"** or **"DOWN"**.

```bash
$ ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP mode DEFAULT group default qlen 1000
    link/ether 12:34:56:78:90:ab brd ff:ff:ff:ff:ff:ff
3: wlan0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/ether ab:cd:ef:12:34:56 brd ff:ff:ff:ff:ff:ff
```

- **`eth0`** is **UP** (active, likely connected via Ethernet).
- **`wlan0`** is **DOWN** (Wi-Fi is disabled).
- **`lo`** (loopback) is always **UP** (used for local communication).

`sudo ip link set eth0 up` enable
`sudo ip link set eth0 down` disable

## _nslookup_

`nslookup domain`
```bash
albertchang ~  $ nslookup google.com
Server: 2401:e180:8d14:2e8a::f2
Address: 2401:e180:8d14:2e8a::f2#53

Non-authoritative answer:
Name: google.com
Address: 142.250.204.46
```

## _check connectivity_

`ping domain`
`traceroute domain`

## _from the other end_

`netstat -an | grep 80 | grep -i LISTEN`
check if port 80 is shown
then run `ip link` , `nslookup`, etc from this end