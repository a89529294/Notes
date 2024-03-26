A _package manager_ is a software tool that helps you install other software. Its primary functions include:

- Downloading software from official sources
- Installing software
- Updating software
- Removing software
- Managing dependencies

## How does a package manager work?

When you type a command like `apt install neovim`, the package manager will:

1. Check to see if the package is already installed.
2. If it's not installed, it will download the package from a repository.
3. It will install the package on your computer.
4. It will install any dependencies that the package needs to run.
5. It will (hopefully) add the package to your PATH if it should be there.

## webi
_webinstall.dev_ is a special package manager that does not need the user to download itself.
For example to download _node_, run 
```bash
curl -sS https://webi.sh/node | sh
```