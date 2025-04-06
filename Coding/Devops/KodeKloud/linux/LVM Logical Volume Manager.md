LVM (Logical Volume Manager) allows flexible disk management. Below are the most useful commands categorized by task.
## **1. Physical Volume (PV) Management**

| Command                  | Description                                            |
| ------------------------ | ------------------------------------------------------ |
| `sudo pvcreate /dev/sdX` | Initialize a disk/partition as an LVM physical volume. |
| `sudo pvdisplay`         | Show details about physical volumes.                   |
| `sudo pvs`               | Brief summary of physical volumes.                     |
| `sudo pvremove /dev/sdX` | Remove a physical volume from LVM.                     |

**Example:**
```bash
sudo pvcreate /dev/sdb           # Make /dev/sdb an LVM PV
sudo pvs                        # List PVs
```

---
## **2. Volume Group (VG) Management**

| Command                          | Description                     |
| -------------------------------- | ------------------------------- |
| `sudo vgcreate vg_name /dev/sdX` | Create a new volume group.      |
| `sudo vgdisplay`                 | Show detailed VG info.          |
| `sudo vgs`                       | Brief summary of volume groups. |
| `sudo vgextend vg_name /dev/sdY` | Add a PV to an existing VG.     |
| `sudo vgreduce vg_name /dev/sdX` | Remove a PV from a VG.          |
| `sudo vgremove vg_name`          | Delete a volume group.          |

**Example:**

```bash
sudo vgcreate my_vg /dev/sdb     # Create VG "my_vg" with /dev/sdb
sudo vgextend my_vg /dev/sdc     # Add /dev/sdc to "my_vg"
sudo vgs                         # List VGs
```

---
## **3. Logical Volume (LV) Management**

| Command                                     | Description                             |
| ------------------------------------------- | --------------------------------------- |
| `sudo lvcreate -L 10G -n lv_name vg_name`   | Create a 10GB LV.                       |
| `sudo lvdisplay`                            | Show detailed LV info.                  |
| `sudo lvs`                                  | Brief summary of logical volumes.       |
| `sudo lvextend -L +5G /dev/vg_name/lv_name` | Increase LV size by 5GB.                |
| `sudo lvreduce -L -2G /dev/vg_name/lv_name` | Reduce LV size by 2GB (**dangerous!**). |
| `sudo lvremove /dev/vg_name/lv_name`        | Delete a logical volume.                |

**Example:**

```bash
sudo lvcreate -L 20G -n my_lv my_vg   # Create 20GB LV "my_lv"
sudo lvextend -L +5G /dev/my_vg/my_lv # Extend "my_lv" by 5GB
sudo lvs                              # List LVs
```

---
## **4. Resizing Filesystems**

After extending an LV, you must resize the filesystem:

| Filesystem | Command                                         |
| ---------- | ----------------------------------------------- |
| **ext4**   | `sudo resize2fs /dev/vg_name/lv_name`           |
| **XFS**    | `sudo xfs_growfs /mount/point`                  |
| **btrfs**  | `sudo btrfs filesystem resize +5G /mount/point` |

**Example (ext4):**

```bash
sudo lvextend -L +10G /dev/my_vg/my_lv  # Extend LV
sudo resize2fs /dev/my_vg/my_lv         # Resize ext4 filesystem
```

---
## **5. Snapshots**

|Command|Description|
|---|---|
|`sudo lvcreate --snapshot -L 5G -n snap_name /dev/vg_name/lv_name`|Create a 5GB snapshot.|
|`sudo lvremove /dev/vg_name/snap_name`|Delete a snapshot.|

**Example:**

```bash
sudo lvcreate --snapshot -L 5G -n snap01 /dev/my_vg/my_lv
```

---
## **6. Advanced Operations**

| Command                                         | Description                     |
| ----------------------------------------------- | ------------------------------- |
| `sudo lvrename vg_name old_lv_name new_lv_name` | Rename an LV.                   |
| `sudo lvchange -ay /dev/vg_name/lv_name`        | Activate an LV.                 |
| `sudo lvchange -an /dev/vg_name/lv_name`        | Deactivate an LV.               |
| `sudo lvscan`                                   | Scan for all LVs on the system. |
|                                                 |                                 |

---
## **7. Troubleshooting**

|Command|Description|
|---|---|
|`sudo vgscan`|Scan for VGs.|
|`sudo pvscan`|Scan for PVs.|
|`sudo lvmdiskscan`|List disks usable by LVM.|

---
### **Summary**

- **PV** → **VG** → **LV** (Physical → Volume Group → Logical Volume).
- **Extend LVs** (`lvextend`) + **resize FS** (`resize2fs`/`xfs_growfs`).
- **Snapshots** allow backups without downtime.