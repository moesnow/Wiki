# Docker

1. Debian
   `sudo apt install -y docker.io`

   Other
    `curl -fsSL get.docker.com | sh -s docker --mirror Aliyun`

2. Optional `sudo vi /etc/docker/daemon.json`

```Vim
{
  "registry-mirrors": ["https://***.mirror.aliyuncs.com"]
}
```

2. `sudo systemctl enable docker`

3. `sudo systemctl start docker`

4. Optional `sudo usermod -aG docker $USER`

