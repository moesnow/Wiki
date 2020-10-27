# Debian

## zh_CN

1. `apt install -y locales`

2. `vi /etc/locale.gen`

```vim
zh_CN.UTF-8 UTF-8
```

3. `locale-gen`

4. `vi /etc/default/locale`

```vim
LANG="zh_CN.UTF-8"
```

## CST

- `apt install -y tzdata && ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime`
