## __Both are Container Orchestrators__ 

- Deploy containers across all available servers.
- Load balancing requests to containers.
- Provide container to container connectivity.
- Restart failed containers.
- Move containers when hosts fail.
## _ECS Elastic Container Service_

- _ECS_ is managed by amazon, you just need to upload config files.
- _Containers_ run on _EC2 instances_ or _Fargate_.
## __Kubernetes__

- Two types of _nodes_
	- _Control plane_ nodes, manager of the cluster
	- _Worker_ nodes, for running containerized workloads
- Users are responsible for both the _control plane_ and _worker_ nodes
## __EKS Elastic Kubernetes Service__

- _EKS_ manages the _control plane_ nodes.
- _Users_ are still responsible for _worker_ nodes.
	- Unless you use _Fargate_, where _AWS_ will mange the _worker_ nodes.
## **Key Differences**

|Feature|ECS|EKS|
|---|---|---|
|**Orchestrator**|AWS proprietary.|Managed Kubernetes (CNCF-compliant).|
|**Learning Curve**|Simpler, AWS-native.|Steeper (Kubernetes expertise needed).|
|**Portability**|Tied to AWS.|Multi-cloud/hybrid-friendly (K8s standard).|
|**Customization**|Limited to AWS tooling.|Highly extensible (K8s plugins, CRDs).|
|**Networking**|Uses AWS VPC/ALB.|Uses Kubernetes CNI (e.g., Calico, AWS VPC CNI).|
|**Pricing**|No control plane cost (pay for resources).|$0.10/hour per cluster (control plane fee).|