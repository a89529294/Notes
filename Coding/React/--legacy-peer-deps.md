## dependencies vs. peerDependencies
- `dependencies` Libraries or modules that an NPM module needs _in order to work_
- `peerDependencies` A peer dependency is a _specific version or set of versions_ of a third-party software library that _a module is designed to work with_. For example, `react-redux` will specify what *versions* of `react` and `redux` it needs. 
- use `npm info module_name peerDependencies` to list a module's `peerdependencies`

## npm v7 + vs. npm v4-6
- v7+
	- installs *specific versions* named by `peerDependencies` by default. If you already have a peerDependency installed but its not listed in the versions required by `peerDependencies` it will throw an error.
	- For example, say `react-redux` listed `react` v16, v17 as `peerDependencies` but you already have `react` v18 installed, npm will throw an error.
	- In order to resolve this, use `npm i --legacy-peer-deps` to ignore this behaviour.
	- using `--legacy-peer-deps` basically reverts back to the same behavior in v4-v6
- v4-v6
	- Does not install versions required in `peerDependencies`
