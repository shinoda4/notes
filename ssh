
## Generate keys

```shell
ssh-keygen -t ed25519 -C "shinoda"

# Send pub key to raspberry pi
ssh-copy-id -i ~/.ssh/id_ed25519.pub mike@10.0.0.99
```

## Edit .ssh config

```text
Host pi
  HostName 10.0.0.99
  User mike
  IdentityFile ~/.ssh/id_ed25519
```
