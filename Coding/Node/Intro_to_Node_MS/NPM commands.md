## Installation
- `npm i package_name`
- `npm i package_name@1.0.0 --save-exact` to install *exact* version; otherwise npm will install latest minor patch.
- `npm i package_name --save-dev` install as dev dependency
- `npm i package_name -g` global installation
- Note that `npm install` and `npm update` are roughly equivalent

## Uninstallation
- `npm un package_name` uninstall package
- `npm un package_name -g` uninstall package from global
- `npm prune` run this after deleting the entries of unused dependencies from `package.json`

## Misc.
- `npm --help` 
- `npm command_name --help` get help for specific command
- `npm list` lists ALL dependencies
- `npm list --depth=n` lists dependencies by levels, `n=0` will give you the same result listed in package.json. 
- `npm outdated` lists packages with newer versions.
