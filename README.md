# ios-deploy 

基于[ios-deploy](https://github.com/ios-control/ios-deploy)扩展，基础能力请参考原项目

## Modify: 查询已安装APP时展示更多信息
命令使用：
```
ios-deploy -B
```

输出：
```
[....] Waiting for iOS device to be connected
CFBundleIdentifier, CFBundleDisplayName, CFBundleVersion, CFBundleShortVersionString
com.apple.mobileslideshow, "照片", "43", "1.0.0"
com.apple.appleseed.FeedbackAssistant, "Feedback", "357", "2.0"
com.alipay.iphoneclient, "支付宝", "10.1.65.6000", "10.1.65"
com.apple.PassbookUIService, "钱包", "1.0", "1.0"
org.videolan.vlc-ios, "VLC", "325", "3.1.9"
com.sogou.sogouinput, "搜狗输入法", "151563", "6.3.2"
```

## Modify: 检测设备时展示iOS版本
命令使用：
```
ios-deploy -c
```

输出：
```
# iOS版本展示原有信息的最后:
[....] Waiting up to 5 seconds for iOS device to be connected
[....] Found 0123456789abcdef0123456789abcdef0123456 (N66AP, iPhone 6s Plus, iphoneos, arm64, 12.0) a.k.a. 'TestIphone' connected through USB.
```

## Add: 根据显示名称卸载App
命令使用：
```
ios-deploy --bundle_name "APP名称" -9
ios-deploy -3 "APP名称" -9
```
输出：
```
# 成功时：
[....] Waiting for iOS device to be connected
------ Search app name phase ------
[ OK ] Bundle id for "APP名称" is com.test.app
------ Uninstall phase ------
[ OK ] Uninstalled package with bundle id com.test.app

# 失败时：
[....] Waiting for iOS device to be connected
------ Search app name phase ------
[ !! ] [ ERROR ] Can't find the app named "APP名称"
```
## Modify：App Store/企业证书的APP也能访问沙盒 /Documents目录
之前默认访问沙盒**根**目录，所以对于App Store/企业证书的APP 则访问失败

## Add：文件浏览/下载/上传/删除支持沙盒路径 & 系统路径
> 之前只能支持文件沙盒路径。
命令使用
```
# 获取相册
ios-deploy -i 0123456789abcdef0123456789abcdef0123456 -f -l/DCIM

# 下载指定文件： 
ios-deploy -i 0123456789abcdef0123456789abcdef0123456 -f -w/DCIM/100APPLE/IMG_001.jpg

# 删除指定文件： 
ios-deploy -i 0123456789abcdef0123456789abcdef0123456 -f -R /DCIM/100APPLE/IMG_001.jpg
```
