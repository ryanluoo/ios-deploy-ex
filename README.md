ios-deploy 
==========

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
ios-deploy --uninstall_by_name "APP名称"
ios-deploy -8 "APP名称"
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
