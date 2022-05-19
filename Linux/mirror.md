# mirror

> https://mirrors.aliyun.com/
>
> https://mirrors.huaweicloud.com/
>
> https://mirrors.tuna.tsinghua.edu.cn/
>
> https://mirrors.cloud.tencent.com/
>
> https://mirrors.ustc.edu.cn/

### Debian

- `sed -i 's/deb.debian.org/mirrors.aliyun.com/g' /etc/apt/sources.list`

- `sed -i 's/deb.debian.org/mirrors.huaweicloud.com/g' /etc/apt/sources.list` support arm64

### Ubuntu

- `sed -i 's/archive.ubuntu.com/mirrors.aliyun.com/g' /etc/apt/sources.list && sed -i 's/security.ubuntu.com/mirrors.aliyun.com/g' /etc/apt/sources.list`

### Alpine

- `sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories`

### OpenWrt

- `sed -i 's/downloads.openwrt.org/mirrors.aliyun.com\/openwrt/g' /etc/opkg/distfeeds.conf`
- `sed -i 's/downloads.openwrt.org/mirrors.cloud.tencent.com\/openwrt/g' /etc/opkg/distfeeds.conf`

### Pypi

- `python3 -m pip config set global.index-url https://mirrors.aliyun.com/pypi/simple/`

### NPM

- `npm config set registry https://registry.npmmirror.com/ && npm cache clean -f`
