# mirror

> http://mirrors.aliyun.com/

### Debian

- `sed -i 's/deb.debian.org/mirrors.aliyun.com/g' /etc/apt/sources.list`

- `sed -i 's/deb.debian.org/mirrors.huaweicloud.com/g' /etc/apt/sources.list` support arm64

### Ubuntu

- `sed -i 's/archive.ubuntu.com/mirrors.aliyun.com/g' /etc/apt/sources.list && sed -i 's/security.ubuntu.com/mirrors.aliyun.com/g' /etc/apt/sources.list`

### Alpine

- `sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories`

### Pypi

- `python3 -m pip config set global.index-url https://mirrors.aliyun.com/pypi/simple/`

### NPM

- `npm config set registry https://registry.npm.taobao.org/ && npm cache clean -f`
