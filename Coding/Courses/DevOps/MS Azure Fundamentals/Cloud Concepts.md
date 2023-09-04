## What is Cloud Computing
The delivery of _computing services over the internet_. 
_Computing services_ include common IT infrastructure such as virtual machines, storage, databases, and networking. Newer services include Internet of Things (IoT), machine learning (ML), and artificial intelligence (AI).

## Shared Responsibility Model
With an _on-premises datacenter_, you’re responsible for everything. With cloud computing, those responsibilities shift. The shared responsibility model is heavily tied into the cloud service types (covered later in this learning path): _infrastructure as a service_ (IaaS), _platform as a service_ (PaaS), and _software as a service_ (SaaS). IaaS places the most responsibility on the consumer, with the cloud provider being responsible for the basics of physical security, power, and connectivity. On the other end of the spectrum, SaaS places most of the responsibility with the cloud provider. PaaS, being a middle ground between IaaS and SaaS, rests somewhere in the middle and evenly distributes responsibility between the cloud provider and the consumer.
![[shared-responsibility.svg]]
Note: Microsoft here can be replaced with any other cloud provider.

In summary:
You’ll always be responsible for:
- The information and data stored in the cloud
- Devices that are allowed to connect to your cloud (cell phones, computers, and so on)
- The accounts and identities of the people, services, and devices within your organization

The cloud provider is always responsible for:
- The physical datacenter
- The physical network
- The physical hosts

Your service model will determine responsibility for things like:
- Operating systems
- Network controls
- Applications
- Identity and infrastructure


