### Method 1: Install with `rpm -ivh`
#### When to use:
- For quick, one-off installations.
- When you know the package has no dependencies or can handle them manually.
#### Steps:
1. Download the `.rpm` file: `wget https://example.com/path/to/package.rpm`
2. Install the package using `rpm`: `sudo rpm -ivh package.rpm`
    - `-i`: Install the package.
    - `-v`: Verbose output.
    - `-h`: Show progress bar.
#### Notes:
- Does **not** resolve dependencies automatically.
- Use this only if you’re sure the package has no dependencies or you can manually install them.

### Method 2: Install with `yum localinstall`

#### When to use:
- When you want `yum` to handle dependencies automatically.
- For installing local `.rpm` files.
#### Steps:
1. Download the `.rpm` file: `wget https://example.com/path/to/package.rpm`
2. Install the package using `yum localinstall`: `sudo yum localinstall package.rpm`
#### Notes:
- Automatically resolves and installs dependencies from configured repositories.
- Easier and safer than `rpm -ivh` for most use cases.

### Method 3: Add Repository to `/etc/yum.repos.d/`

#### When to use:
- For scalable, maintainable installations.
- When the package is part of a well-maintained repository.
- When you want automatic updates and dependency resolution.
#### Steps:
1. Create a `.repo` file in `/etc/yum.repos.d/`: `sudo vi /etc/yum.repos.d/package_name.repo`
2. Add the repository configuration:
```
[package_name]
    name=Custom Repository
    baseurl=https://example.com/repo
    enabled=1
    gpgcheck=1
    gpgkey=https://example.com/repo/RPM-GPG-KEY-custom
```
1. Clear the yum cache (optional but recommended): `sudo yum clean all`
2. Install the package: `sudo yum install package_name`
#### Notes:
- Automatically resolves dependencies and allows for future updates.
- Ensures secure installations if `gpgcheck` is enabled.
- Best for long-term use and multiple packages from the same repository.