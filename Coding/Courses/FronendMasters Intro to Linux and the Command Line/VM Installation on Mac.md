# Instructions
https://multipass.run/docs/installing-on-macos#heading--use-brew

## install
```bash
brew install multipass
```

## uninstall
```bash
multipass delete --purge --all
brew uninstall --zap multipass
```

## commands
- `multipass version`
- `multipass find` lists all images of ubuntu
- `multipass launch` creates and starts an instance based on the latest ubuntu lts, or you can specify an image
- `multipass shell <instance-name>` 
- `multipass list` lists all instances
- `multipass delete <instance-name>`
- `multipass stop <instance-name>`
- `multipass start <instance-name>`
- `multipass info <instance-name>`

