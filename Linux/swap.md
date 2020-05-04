# swap

## Turn on swap

1. `dd if=/dev/zero of=/mnt/swap bs=1M count=2048`

2. `chmod 600 /mnt/swap && mkswap /mnt/swap`

3. `swapon /mnt/swap`

4. `vi /etc/fstab`

```vim
/mnt/swap swap swap defaults 0 0
```

## swappiness

- cat /proc/sys/vm/swappiness

1. `vi /etc/sysctl.conf`

```vim
vm.swappiness = 1
```

2. `sysctl -p`
