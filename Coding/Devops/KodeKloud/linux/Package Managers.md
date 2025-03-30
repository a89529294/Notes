## dpkg / apt (debian based)
- ubuntu
- debian
- linux mint
- arch linux
- order from left to right, older to newer
## rpm / yum / dnf (rpm based)
- red hat
- centos (forked from red hat, free)
- fedora
- order from left to right, older to newer

## What is a Package

- A compressed archive that contains all the files required by a particular software to run.

## Functions of a Package Manager

- Package integrity and authenticity
- Simplified package management
- Grouping packages
- Managing dependencies

## Working with RPM

Note that `rpm` _does not install dependencies_ of a package. Use yum/dnf for automatic dependency installation.

### Installation
`rpm -ivh telnet.rpm`
- `-i` → Install the package.
- `-v` → Verbose output (shows more details).
- `-h` → Show progress bar with hash marks.
- telnet.rpm must be a _local file path on the system_

### Uninstalling
`rpm -e telnet.rpm`
- `-e` erase

### Upgrade
`rpm -Uvh telnet.rpm`
- `-U` → **Upgrades** the package if installed, otherwise **installs** it.
- `-v` → Verbose output (shows more details).
- `-h` → Show progress bar with hash marks.

### Query
`rpm -q telnet.rpm`
- `-q` query

### Verifying
`rpm -Vf path_to_package`, used to **verify the integrity of installed files** belonging to a package.
- `-V` → Checks whether files from an installed RPM package have been modified, deleted, or had their permissions/ownership changed since installation.
- `-f` (or `--file`) → Specifies that you're verifying files from a **package that owns the given file path** (instead of a package name).

## Working with Yum

YUM repositories are configuration files that tell the **`yum`** or **`dnf`** package managers where to download RPM packages. These repos are stored in specific directories on a Linux system (primarily RHEL, CentOS, Fedora, etc.).

Default yum repository location: `/etc/yum.repos.d/`
- Files have a `.repo` extension (e.g., `CentOS-Base.repo`, `epel.repo`).
- Each `.repo` file contains one or more repository definitions.

### Overview
- `yum install xxx`, xxx _can_ be either a local file path _or_ a URL _or_ a package name
- `yum remove xxx`
- `yum update xxx`

### **1. How `yum install xxx` Finds a Package**

When you run: `yum install package-name`
YUM/DNF does the following:

#### **Step 1: Read Repository Metadata**

- Checks all **enabled** `.repo` files in `/etc/yum.repos.d/`.
- **Downloads fresh metadata** (unless cached) for each repo, including:
    - Package lists (`primary.xml.gz`).
    - Dependency info (`filelists.xml.gz`).
    - Checksums (`repomd.xml`).

#### **Step 2: Search for the Package**

- Scans **all enabled repos** (in the order they’re listed) for `package-name`.
- **Priority rules**:
    - If the same package exists in multiple repos, the one with the **highest version** is chosen.
    - If versions are equal, the repo listed **first** in alphabetical order (by `.repo` filename) wins.
        
#### **Step 3: Resolve Dependencies**

- Finds all required dependencies (also checking across repos).
- **Conflict resolution**: Skips packages that break existing installs (unless `--skip-broken` is used).

#### **Step 4: Download & Install**

- Downloads the RPM(s) from the best-matched repo.
- Installs them using `rpm -i`.
    
---

### **2. Example: Installing `nginx`**

`yum install nginx`

1. **Checks repos** like `base`, `epel`, `updates` (if enabled).
2. **Finds `nginx`** in `epel` (assuming `base` doesn’t have it).
3. **Downloads** from `epel`’s `baseurl` (e.g., `https://download.fedoraproject.org/pub/epel/...`).
4. **Installs** it + dependencies (e.g., `openssl`, `pcre`).
    
---

### **3. How to See Which Repo a Package Comes From**

Use: `yum info package-name`

or:

`dnf --disablerepo=* --enablerepo=epel list package-name`

**Example output for `nginx`**:

```
Available Packages
nginx.x86_64  1:1.20.1-1.el8  epel
```
Shows `nginx` is from the `epel` repo.

---

### **4. Key Behaviors to Know**

- **Repo priority**: If two repos have the same package, the **newer version** wins.
    - To enforce repo priority, use `priority=N` in `.repo` files (lower number = higher priority).
- **Excluding repos**: Skip a repo with `--disablerepo=repo-name`.
- **Forcing a repo**: Install only from a specific repo:
	`yum --disablerepo=* --enablerepo=epel install nginx`
    
---

### **5. Troubleshooting**

#### **"No match for argument: package-name"**

- The package doesn’t exist in **any enabled repo**.
- **Fix**: Check repos with: `yum repolist`. Then enable the correct repo (e.g., `epel`).


## Working with DPKG

No automatic dependency management

- `dpkg -i telnet.deb` install
- `dpkg -r telnet.deb` remove
- `dpkg -l telnet` list
- `dpkg -s telnet` status
- `dpkg -p <path-to-file>` info

## Working with APT

`/etc/apt/sources.list`, similar to `/etc/yum.repos.d/`

- `apt update`, immediately after installing the os
- `apt upgrade` 
- `apt edit-sources`, edit `/etc/apt/sources.list`
- `apt install telnet`
- `apt remove telnet`
- `apt search telent`
- `apt list`, `apt list | grep telnet`