While virtual machines are an excellent way to reduce costs versus the investments that are necessary for physical hardware, they're still limited to a single operating system per virtual machine. _If you want to run multiple instances of an application on a single host machine, containers are an excellent choice_.

## VM vs Containers
_VMs_ virtualize the hardware, _containers_ virtualize the os.

## Azure Container Instances
Azure Container Instances offer the fastest and simplest way to run a container in Azure

## Azure Container Apps
Azure Container Apps are similar in many ways to a container instance.
Container Apps have extra benefits such as the ability to incorporate load balancing and scaling.

## Azure Kubernetes Service
Azure Kubernetes Service (AKS) is a container orchestration service. An orchestration service manages the lifecycle of containers. When you're deploying a fleet of containers, AKS can make fleet management simpler and more efficient.

## Using containers
Containers are often used to create solutions by using a microservice architecture. This architecture is where you break solutions into smaller, independent pieces. For example, you might _split a website into a container hosting your front end, another hosting your back end, and a third for storage_. This split allows you to separate portions of your app into logical sections that can be maintained, scaled, or updated independently.


