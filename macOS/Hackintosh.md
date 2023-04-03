# Hackintosh

## 强制开启独显DRM解码

解决Apple DRM内容不能打开问题

> https://macoshome.com/hackintosh/hcourse/9581.html

打开终端依次输入命令运行：

```bash
defaults write com.apple.AppleGVA gvaForceAMDKE -bool YES
defaults write com.apple.AppleGVA gvaForceAMDAVCEncode -bool YES
defaults write com.apple.AppleGVA gvaForceAMDAVCDecode -bool YES
defaults write com.apple.AppleGVA gvaForceAMDHEVCDecode -bool YES
```

这个操作之后剪辑视频时候核显就不参与视频解码加速。

恢复命令：

```bash
defaults write com.apple.AppleGVA gvaForceAMDKE -bool no
defaults write com.apple.AppleGVA gvaForceAMDAVCEncode -bool no
defaults write com.apple.AppleGVA gvaForceAMDAVCDecode -bool no
defaults write com.apple.AppleGVA gvaForceAMDHEVCDecode -bool no
```



## 黑苹果无线网卡指南

> https://dortania.github.io/Wireless-Buyers-Guide/Airport.html#socketed-cards

