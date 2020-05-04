# Docker

1. `curl -fsSL get.docker.com | sh -s docker --mirror Aliyun`

2. `vi /etc/docker/daemon.json`

```Vim
{
  "registry-mirrors": ["https://***.mirror.aliyuncs.com"]
}
```

2. `systemctl enable docker`

3. `systemctl start docker`

4. `usermod -aG docker $USER`

