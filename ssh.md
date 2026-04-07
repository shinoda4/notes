
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

## 反向SSH隧道流量

在本机开启代理后，开启局域网代理，比如端口 `7890`，`ssh` 连接到 `remote_server`

```shell
ssh -R 8888:127.0.0.1:7890 user@remote_server
```

然后在 `remote_server` 输入

```shell
export http_proxy=127.0.0.1:8888
export https_proxy=127.0.0.1:8888
```
## 本地端口转发 (Local Port Forwarding)

将远端的 `9090` 端口转发到本地的 `8080`

```shell
# ssh -L [本地地址:]本地端口:目标地址:目标端口 用户名@跳板机地址
ssh -L 8080:localhost:9090 remote_server
```

