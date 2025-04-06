## account

### /etc/passwd
 
 This file __contains all accounts__.
 
```txt
root:x:0:0:root:/root:/bin/bash
ubuntu:x:1000:1000:Ubuntu:/home/ubuntu:/bin/bash
```
- Each line follows this format: `username:password:UID:GID:GECOS:home_directory:shell`
- **Username**: The login name of the user (e.g., root, ubuntu).
- **Password**: Historically, this field stored the encrypted password, but on modern systems, it typically contains an x, indicating that the password is stored in a separate file (/etc/shadow) for security reasons.
- **UID (User ID)**: A unique numerical identifier for the user (e.g., 0 for root, 1000 for a typical first regular user like ubuntu).
- **GID (Group ID)**: The numerical identifier of the primary group the user belongs to (e.g., 0 for the root group).
	- when a user is created without explicitly specifying a group, the system typically creates a new group with the same name and ID as the user and assigns it as the user’s _primary group_.
- **GECOS**: Optional field for additional user information (e.g., full name, phone number), often left blank or used for a description (e.g., Ubuntu for the ubuntu user).
- **Home Directory**: The path to the user's home directory (e.g., /root for root, /home/ubuntu for ubuntu).
- **Shell**: The default shell or command interpreter for the user (e.g., /bin/bash for an interactive shell, /usr/sbin/nologin to prevent login).

### /etc/sudoers

Defines what a __user or group can do when using the `sudo` command__.

```txt
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo ALL=(ALL:ALL) ALL
```
### user related commands

- `id ubuntu`
```txt
uid=1000(ubuntu) gid=1000(ubuntu) groups=1000(ubuntu),4(adm),24(cdrom),27(sudo),30(dip),105(lxd)
```
- `who` check who is logged in
- `last` shows all log in records
- `whoami` check current user
### Types of accounts

Based on their purpose and characteristics, accounts in /etc/passwd can be categorized into several types. Here are the main ones, with examples from the file you shared earlier:

#### 1. **Superuser (Root) Account**

- **Purpose**: The administrative account with unrestricted access to the system.
- **Characteristics**:
    - UID is always 0.
    - Has full privileges (can read/write/execute any file, manage all processes, etc.).
    - Typically has an interactive shell (e.g., /bin/bash).
- **Example**: root:x:0:0:root:/root:/bin/bash
- **Notes**: There’s only one root account, though multiple users can have UID 0 (less common and risky).

#### 2. **System Accounts**

- **Purpose**: Used by the operating system or services to run background processes, daemons, or manage resources.
- **Characteristics**:
    - UIDs are typically low (e.g., 1–999), though conventions vary by distribution.
    - Often have a non-login shell (e.g., /usr/sbin/nologin or /bin/false) to prevent interactive logins.
    - Home directories may be set to non-existent or system-specific paths (e.g., /nonexistent, /var/run).
- **Examples**:
    - daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin (for background processes).
    - www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin (for web servers like Apache).
    - systemd-network:x:998:998:systemd Network Management:/:/usr/sbin/nologin (for systemd services).
- **Notes**: These accounts isolate system processes for security and don’t represent human users.

#### 3. **Regular User Accounts**

- **Purpose**: Created for human users or interactive logins (e.g., system administrators, developers, or end users).
- **Characteristics**:
    - UIDs are typically higher (e.g., 1000 and above) to distinguish them from system accounts.
    - Have a valid home directory (e.g., /home/username).
    - Assigned an interactive shell (e.g., /bin/bash, /bin/sh).
- **Example**: ubuntu:x:1000:1000:Ubuntu:/home/ubuntu:/bin/bash
- **Notes**: These are the accounts people use to log in and perform tasks. They often have a private group (GID matching UID) by default.

#### 4. **Pseudo-User Accounts**

- **Purpose**: Special accounts that don’t fit neatly into the above categories, often used for specific software or compatibility.
- **Characteristics**:
    - May have high UIDs (e.g., 65534) or unique roles.
    - Often lack a proper home directory or shell.
- **Examples**:
    - nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin: A generic unprivileged account used by processes that need minimal permissions (e.g., NFS, some daemons).
- **Notes**: nobody is a common pseudo-user to run untrusted or low-privilege tasks.

#### 5. **Service-Specific Accounts**

- **Purpose**: Created for specific applications or services, often during software installation.
- **Characteristics**:
    - Similar to system accounts but tied to a particular service or daemon.
    - UIDs can vary (often in the system range or dynamically assigned).
    - Shell is typically non-login, and home directories are service-specific.
- **Examples**:
    - sshd:x:105:65534::/run/sshd:/usr/sbin/nologin (for the SSH daemon).
    - _chrony:x:110:112:Chrony daemon,,,:/var/lib/chrony:/usr/sbin/nologin (for Chrony time sync).
    - polkitd:x:989:989:User for polkitd:/:/usr/sbin/nologin (for PolicyKit).
- **Notes**: These are more granular than generic system accounts and are often created by package managers (e.g., apt on Debian-based systems).


### Additional Notes

- **UID Ranges**: While not strictly enforced, conventions often dictate:
    - 0: Root.
    - 1–999: System and service accounts (some distros use 1–499 for system, 500–999 for services).
    - 1000+: Regular users.
- **Login Capability**: Accounts with shells like /usr/sbin/nologin or /bin/false can’t log in interactively, distinguishing system/service accounts from regular users.
- **Dynamic Creation**: Package installations (e.g., apt install ssh) often add service accounts to /etc/passwd.

In summary, /etc/passwd does contain all accounts, and they fall into categories like superuser, system, regular, pseudo-user, and service-specific accounts, each serving distinct roles in the system!
## group

`/etc/group`
```txt
root:x:0:
ubuntu:x:1000:
```
- Each line follows this format: `group_name:password:GID:group_members`
- **Group Name**: The name of the group (e.g., root, sudo).
- **Password**: Historically used to store an encrypted group password, but this is rarely used today. It’s typically an x (indicating the password is in /etc/gshadow, if used) or left blank.
- **GID (Group ID)**: A unique numerical identifier for the group (e.g., 0 for root, 1000 for a user-specific group like ubuntu).
- **Group Members**: A comma-separated list of usernames that are members of the group (e.g., ubuntu in the sudo group). This field only lists _secondary_ group memberships; a user’s _primary_ group is defined by the GID in /etc/passwd.