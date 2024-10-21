You can use one pair of public and private keys for accessing all servers, including github, your DO droplets, etc.
You can simply modify `./ssh/config` to
```
Host *
  IdentityFile id_rsa
```
Make sure to add the corresponding public key file `id_rsa.pub`'s content to the `~/.ssh/authorized_keys` file on the remote servers.