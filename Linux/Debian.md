# Debian

## zh_CN

1. `sudo apt install -y locales`

2. `sudo vim /etc/locale.gen`

```vim
zh_CN.UTF-8 UTF-8
```

3. `sudo locale-gen && sudo update-locale LANG="zh_CN.UTF-8"`

## CST

- `sudo apt install -y tzdata && sudo ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime`

## zram

1. `sudo apt install zram-tools`
2. `echo -e "ALGO=zstd\nPERCENT=60" | sudo tee -a /etc/default/zramswap`
3. `sudo systemctl reload zramswap.service`
