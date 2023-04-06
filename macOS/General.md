# General

## Dock栏无延迟

```bash
defaults write com.apple.Dock autohide-delay -float 0 && killall Dock
```

# 解除Time Machine限速

```bash
sudo sysctl debug.lowpri_throttle_enabled=0
```


