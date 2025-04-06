## View on phone
https://dashboard.ngrok.com/get-started/setup/macos

## Remote debug android devices
https://developer.chrome.com/docs/devtools/remote-debugging/

## easiest method

- Make sure laptop and phone is on the same network
- Run app on laptop, note the port
- Find laptops local ip address, two ways
	- top left mac icon -> system settings -> Wifi -> click on Details -> TCP/IP tab -> IP address
	- `ifconfig | grep -A 5 en0` find `inet 192.168.149.179 netmask 0xffffff00 broadcast`
- Back on phone, in url bar type `http://192.168.149.179:port`