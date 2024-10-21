## ## Scale VMs in Azure
Azure can also manage the grouping of VMs for you with features such as _scale sets_ and _availability sets_.

### Virtual machine scale sets
Virtual machine scale sets let you create and manage a group of _identical, load-balanced VMs_.
he number of VM instances can automatically increase or decrease in response to demand, or you can set it to scale based on a defined schedule. Virtual machine scale sets also _automatically deploy a load balancer_ to make sure that your resources are being used efficiently.

### Virtual machine availability sets
Virtual machine availability sets are another tool to help you build a more _resilient, highly available environment_.
- **Update domain**: The update domain groups VMs that can be rebooted at the same time. This allows you to apply updates while knowing that only one update domain grouping will be offline at a time.
- **Fault domain**: The fault domain groups your VMs by common power source and network switch. By default, an availability set will split your VMs across up to three fault domains.
