There are three types of storage, _block storage_, _file storage_, and _object storage_.

## __Block Storage EBS__
### **1. What is Block Storage?**

Block storage is a type of data storage where information is stored in fixed-sized chunks called **blocks**. Each block has a unique address, and the storage system (like a SAN, SSD, or HDD) manages these blocks independently. Unlike file storage (which deals with files and folders) or object storage (which deals with objects and metadata), block storage is raw and unstructured.

Key properties:
- Blocks are low-level storage units (typically 512 bytes, 4KB, etc.).
- The OS or filesystem manages how these blocks are organized.
- Block devices don’t inherently understand files—they just read/write blocks.

Examples of block storage devices:
- Hard Disk Drives (HDDs)
- Solid-State Drives (SSDs)
- Storage Area Network (SAN) LUNs
- Cloud block storage (AWS EBS, Azure Disk, Google Persistent Disk)
---
### **2. How Blocks Are Presented as a "Volume" to the OS**

When you connect a block storage device (like a disk) to a computer, the OS sees it as a **raw block device** (e.g., `/dev/sda` in Linux or `Disk 0` in Windows). However, this raw device is just a sequence of blocks—it doesn’t yet have a filesystem.

#### **Steps to Make It Usable:**

1. **OS Detects the Block Device**
    - The storage controller (e.g., SATA, NVMe, iSCSI) presents the blocks as a single contiguous device.
    - Example: In Linux, it appears as `/dev/sdb` (for a secondary disk).
2. **Create a Partition (Optional but Common)**
    - The OS can split the block device into logical sections called **partitions** (e.g., `/dev/sdb1`).
    - Partitions help organize storage (e.g., one for the OS, one for data).
3. **Format with a Filesystem**
    - The OS runs a tool (like `mkfs` in Linux or Disk Management in Windows) to create a filesystem (e.g., ext4, NTFS) on the partition.
    - The filesystem structures the blocks into directories and files.
4. **Mount the Filesystem**
    - The OS "mounts" the filesystem to a directory (e.g., `/mnt/data`), making it usable for storing files.

#### **Analogy:**

Think of block storage like a **blank notebook**:
- The notebook has many pages (blocks).
- You can decide how to organize the pages (partitioning).
- You then add a table of contents and structure (filesystem) to make it useful.

---
### **3. How a Block Device Can Be Bootable**

For a block device to be bootable:
1. **It Needs a Bootloader**
    - The first block(s) of the disk typically contain a **bootloader** (e.g., GRUB, Windows Boot Manager).
    - The bootloader tells the BIOS/UEFI how to start the OS.
2. **It Must Have a Recognized Partition Scheme**
    - For BIOS: Usually uses **MBR** (Master Boot Record) partitioning.
    - For UEFI: Usually uses **GPT** (GUID Partition Table) with an **EFI System Partition (ESP)**.
3. **It Must Contain an OS with a Valid Filesystem**
    - The OS is installed by copying its files to the block device (after partitioning and formatting).
    - Example: When you install Linux, the installer:
        - Creates partitions (e.g., `/`, `/boot`, `swap`).
        - Formats them with filesystems (e.g., ext4 for `/`, FAT32 for `/boot/efi`).
        - Copies OS files and installs the bootloader.
4. **BIOS/UEFI Recognizes It as Bootable**
    - The firmware (BIOS/UEFI) reads the bootloader from the disk and starts the OS.
---
### **4. Why This Can Be Confusing**

- **Block Storage is Raw**: Without a filesystem, it’s just a pile of blocks—no files or folders.
- **Filesystem Adds Structure**: The OS uses the filesystem to organize blocks into something usable.
- **Bootable Means "Ready to Run an OS"**: A bootable disk has:
    - A partition table (MBR/GPT).
    - A bootloader.
    - An OS with a valid filesystem.
---
### **5. Example Workflow (Installing an OS on a Block Device)**

1. You attach a new SSD to your computer (seen as `/dev/sdb`).
2. You partition it:
    - `/dev/sdb1` (EFI System Partition, FAT32, 500MB)
    - `/dev/sdb2` (Root partition, ext4, rest of disk)    
3. You format:
    - `mkfs.fat -F32 /dev/sdb1` (for ESP)
    - `mkfs.ext4 /dev/sdb2` (for root)
4. You install the OS:
    - Mount `/dev/sdb2` to `/mnt`.
    - Copy OS files (e.g., Linux kernel, apps).
    - Install bootloader to `/dev/sdb`.
5. Reboot, and BIOS/UEFI loads the OS from the SSD.
---
### __EBS and EC2__

- **Attachable/Detachable**: Just like plugging in a USB drive to your computer, you can attach/detach EBS volumes to EC2 instances (though they must be in the same AWS Availability Zone).
- **Persistent Storage**: Unlike the **instance store** (temporary storage that dies with the instance), EBS volumes **persist independently** of the EC2 instance. If the instance stops or terminates (unless set to delete on termination), the EBS volume remains.
- **Uses**:
    - **Root Volume (`/dev/sda1`)** → Typically holds the OS (like your `aws-simple-hono-be` instance).
    - **Additional Volumes (`/dev/sdf`, `/dev/xvdb`, etc.)** → Extra storage for apps, databases, logs, etc.
#### **Key Features**

|Feature|Description|
|---|---|
|**Types**|SSD (gp3, io1/io2) for speed, HDD (st1, sc1) for cheap bulk storage|
|**Snapshots**|Backup your EBS volume to S3 (like saving a copy of your hard drive).|
|**Resizing**|Increase size or change type **without downtime** (modern volumes).|
|**Encryption**|Supports encryption at rest (AWS KMS).|

#### **Your Case (`/dev/sda1`)**

- This is the **root volume** (like the `C:\` drive on Windows) for your instance `i-07b725...`.
- If the instance was launched from an **AMI (Amazon Machine Image)**, this EBS volume contains the OS, apps, and data.
- By default, deleting the instance **also deletes this volume** (unless you disabled "Delete on Termination" during setup).

#### **When Would You Use EBS?**

- Need **durable storage** beyond the instance’s lifetime? → EBS.
- Running a database (e.g., MySQL, PostgreSQL)? → EBS.
- Want frequent backups? → Use **EBS Snapshots**.

### **Summary**

**"EBS is a virtual hard drive for your EC2 instance."**
#### **Just Like a Physical Hard Drive:**

- You **attach it** to an EC2 instance (like plugging in a USB drive).
- It stores data **even after the instance stops** (unlike temporary instance storage).
- You can **detach it** and move it to another EC2 instance (if they're in the same AWS region/AZ).
- You can **increase its size** or **take backups** (snapshots).
#### **Real-World Analogy:**

- Think of **EC2 as a computer** (CPU + RAM).
- **EBS is its SSD/HDD** (where the OS, apps, and files live).

## __EFS Elastic Filesystem__

- A **managed NFS (v4.1)** file system for Linux workloads.
- **Shared storage** accessible by multiple EC2 instances, containers, or Lambda functions concurrently.

## __Object Storage S3__

- _Objects_ are nothing more than files
- Does not have a folder structure, everything is in the same folder
- Great for logs and media files