Containers have their own _processes_, _network_, and _mounts_, but they share the _os kernel_.

- **Docker images (ubuntu, centos, etc.) are just pre-packaged software environments** that run on top of the host’s Linux kernel.
	- Filesystem (`/bin`, `/lib`, etc.).
	- Userland tools (`apt`, `yum`, `bash`).
	- Configs (e.g., `/etc` files).
- **Containers share the host’s OS kernel** (if the host is Linux).
    - **On Linux hosts**: Containers directly use the host’s kernel (no VM).
    - **On Mac/Windows**: Containers run inside a **Linux VM**, so they share the _VM’s_ kernel, not the host’s macOS/Windows kernel.
- The point of Docker is to package applications and their dependencies into lightweight, portable, isolated environments that run consistently across any system.
## __Operating System__

An _operating system_ Consists of two things, _a set of software_ and _os kernel_.
- _os kernel_ is responsible for interacting with the underlying hardware
- Ubuntu, Red Hat Enterprise Linux (RHEL), CentOS, and most other Linux distributions **use the same Linux kernel** (the core of the operating system) at their base.
- However, **different distributions may use different versions or patches** of the kernel depending on their needs.
- Its the softwares that each distribution/os uses that make them different.

## __Container__ vs __Image__

- __image__
	- template
	- plan
	- blueprint
- __container__
	- running instances of image