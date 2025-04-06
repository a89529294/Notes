## __aws ec2 example__

- `lsblk`
```bash
NAME     MAJ:MIN RM  SIZE RO TYPE MOUNTPOINTS
loop0      7:0    0 26.3M  1 loop /snap/amazon-ssm-agent/9881
loop1      7:1    0 73.9M  1 loop /snap/core22/1748
loop2      7:2    0 44.4M  1 loop /snap/snapd/23545
loop3      7:3    0 44.4M  1 loop /snap/snapd/23771
loop4      7:4    0 73.9M  1 loop /snap/core22/1802
xvda     202:0    0    8G  0 disk 
├─xvda1  202:1    0    7G  0 part /
├─xvda14 202:14   0    4M  0 part 
├─xvda15 202:15   0  106M  0 part /boot/efi
└─xvda16 259:0    0  913M  0 part /boot
```
- `df -h / /boot /boot/efi`
```bash
Filesystem      Size  Used Avail Use% Mounted on
/dev/root       6.8G  2.8G  4.0G  41% /
/dev/xvda16     881M  137M  683M  17% /boot
/dev/xvda15     105M  6.1M   99M   6% /boot/efi
```

## __prepare and use a new disk__

### **1. Create a Partition**
Use `gdisk` (for GPT) or `fdisk` (for MBR) to create a partition:
`sudo gdisk /dev/vdb`

- **Inside `gdisk`**:
    - Press `n` (new partition).
    - Accept defaults (partition number `1`, first sector `2048`).
    - For size, type `+500M` (or press `Enter` to use the whole disk).
    - Press `w` to save and exit.

---
#### **2. Format the Partition**

Choose a filesystem (e.g., `ext4` for Linux, `xfs` for AWS, `fat32` for USB):
`sudo mkfs.ext4 /dev/vdb1`

---
#### **3. Mount the Partition**

Create a mount point and mount the partition:
```bash
sudo mkdir /mnt/mydata                # Create a directory to mount to
sudo mount /dev/vdb1 /mnt/mydata      # Mount the partition
```

---
#### **4. Verify It Worked**
```bash
mount | grep /dev/vdb1

# Check disk usage
df -h /mnt/mydata    

# Verify partition layout
lsblk /dev/vdb   

# Check filesystem
sudo blkid /dev/vdb1
```

#### __5.  Make the mount persistent after reboot__
```bash
echo "/dev/vdb1 /mnt/mydata ext4 defaults 0 0" | sudo tee -a /etc/fstab

# `0 0` is fine for `/mnt/data` (no `fsck` needed).
# Use `0 2` only for system partitions (e.g., `/home`, `/var`).
```

## __External Storage__

### DAS Direct Attached Storage

- **What it is**: Storage directly connected to a single server or computer (e.g., internal HDD, external USB drive).
- **Pros**: Fast (no network latency), simple setup.
- **Cons**: Not shared; limited scalability.
- **Use case**: Local storage for a single machine.
### NAS Network Attached Storage

- **What it is**: Storage accessed over a network (e.g., file server, Synology/QNAP devices).
- **Pros**: Shared access, easy to manage, good for small teams.
- **Cons**: Slower than DAS (network-dependent).
- **Use case**: Centralized file storage for multiple users.
### SAN Storage Area Network

- **What it is**: High-speed, block-level storage network (e.g., Fibre Channel, iSCSI).
- **Pros**: Extremely fast, scalable, enterprise-grade.
- **Cons**: Expensive, complex setup.
- **Use case**: Databases, virtualization, large-scale enterprise storage.

### Summary

- Need personal storage? → **DAS**    
- Sharing files in an office? → **NAS**
- Running critical enterprise apps? → **SAN**

## __LVM Logical Volume Manager__

1. **Create a PV (Physical Volume)**
    `sudo pvcreate /dev/sdb`
2. **Create a VG (Volume Group)**
    `sudo vgcreate vg_data /dev/sdb`
3. **Create an LV (Logical Volume)**
    `sudo lvcreate -L 20G -n lv_home vg_data`
4. **Format & Mount**
    `sudo mkfs.ext4 /dev/vg_data/lv_home`
    `sudo mount /dev/vg_data/lv_home /mnt/data`
5. **Persist across reboot**
	 `echo "/dev/vg_data/lv_home /mnt/data ext4 defaults 0 0" | sudo tee -a /etc/fstab`