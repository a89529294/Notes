## network access prereq
- check vm instance if ssh is open
- `sudo systemctl status sshd`
	- if ssh is not running, 
	- `sudo systemctl start sshd`
	- `sudo systemctl enable sshd`
	- if ssh is not installed 
		- `sudo yum update -y`
		- `sudo yum install openssh-server -y`
		- `sudo systemctl start sshd`
		- `sudo systemctl enable sshd`
		- `sudo firewall-cmd --permanent --add-service=ssh`
		- `sudo firewall-cmd --reload`
		- `sudo firewall-cmd --list-services`
		- finally check `sudo systemctl status sshd`
## host only network (method one, cannot connect to outside world)
- open virtualbox
- top left, under File -> Tools -> Network Manager
- create a network, name it vboxnet0, vboxnet1, etc
- Note the lower bound, something like `192.168.56.1`. This would be your host's local ip in this network.
- right click vm, settings -> expert -> network
- select Attached to: Host-only Network
- under name: select the one just created 
- turn on vm, type `ipconfig` in terminal, you should see something like `192.168.56.2`. This is your vm's ip on this network.
- `ping 192.168.56.1` on vm, `ping 192.168.56.2` on host to make sure it works
- `ssh username@192.168.56.2` on host to connect to vm

## port forwarding (NAT, method 2)
- open virtualbox
- right click on vm instance and choose settings, under expert -> network, 
- select Attached to: NAT
- click on port forwarding, then add a new rule
	- name: SSH PORT
	- host port: 2222
	- guest port: 22
- then on host machine, `ssh username@127.0.0.1 -p 2222`, then enter password

## NAT Network
- set it up in almost the same way as host only network

Bridge
- Simply go to vm settings, expert -> network
- Attached to: Bridge Adapter
- to get local ip of host, top left apple icon -> system settings -> wifi -> details -> tcp/ip
- to get local ip of vm, `ifconfig`
- they both should start with 192.168

## Summary
- **NAT (Network Address Translation):** The VM shares the host's IP address and connects to the internet through it. The host acts as a router, translating the VM's traffic. Good for basic internet access, but external devices can't directly reach the VM. *Good for vms to connect to outside world, use port forwarding to allow host to ssh into vm.*
	- allow connection to the internet, not from
	- allow host to ssh into vm
  
- **NAT Network:** Similar to NAT, but allows multiple VMs to share a private network while still using the host's IP for external access. VMs can communicate with each other, but external initiation to the VMs is limited.
	- allow connection to the internet, not from
  
- **Bridged:** The VM gets its own IP address on the same network as the host, appearing as a separate device. It’s fully accessible from the network, ideal for servers or when direct external access is needed.
	- allow connection to and from the internet
	- allow host to ssh into vm
  
- **Host-Only:** The VM is connected to a private network with the host, isolated from the external network. Useful for testing or local host-VM communication, but no internet access unless configured otherwise.
	- allow host to ssh into vm
	- no internet connection