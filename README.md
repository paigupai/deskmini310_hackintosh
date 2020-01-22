
# deskmini310_hackintosh
猿でもわかるhackintosh（MACOS 10.15版)  
本教程使用xjn已打包好的10.15.1镜像，是基于OpenCore来引导黑苹果，教程仅供参考

### 配置

| 配置 | 型号 |
|:-----------|:------------:|
| CPU       |     i3 9100     |
| 内存     |    column    |
| ssd       |     WD Blue SN550 NVMe WDS500G2B0C     |
| 网卡         |      暂无      |
| 显示器       |    center    |

### 状况

* DP: 完美，可以dp转hdmi同样没问题
* hdmi: 可双屏，但是不能单hdmi，会卡引导
* 睡眠: 完美
* 蓝牙/WIFI: 没有设备未测试(理论上免驱的网卡如dw1830等，可以完美支持)
* 有线网卡: OK
* 声卡: OK
* USB: 键鼠usb等ok，但是插入TP LINK Archer T2UH无反应
* USB TYPE C: 未测试

### BIOS设置

* Load UEFI Defaults
 * Advanced
    * Onboard HD Audio: Enabled
      USB Configuration, XHCI Hand-off, Enabled  （关键）  
      ~~ Super IO Configuration, Serial Port, Disabled（必须）~~（BIOS 4.2中Super IO Configuration被删除了，无法修改）   
      Security Secure Boot, Disabled(by default)

CSM disable

CFG Lock: Disabled (关键，在cpu的c-state/status设置里）

### 安装
请参考[xjn的超级小白教程](https://blog.xjn819.com/?p=7#comment-464)最新为10.15.1  
直接下载镜像，写入到u盘即可，如果嫌百度网盘慢，可以冲3块钱用[速盘](https://www.speedpan.com/)  
※注意这个教程中安装的是基于OpenCore的引导，而非clover，所有基于clover引导的修改都是不行的，如果之前安装过clover黑苹果🍎，是无法直接使用的（[参考](https://blog.daliansky.net/OpenCore-BootLoader.html)）  
#### 修改序列号3码
~~ 不影响使用，不介意的人可以跳过，可在windows环境修改  
修改序列号需要编辑config.plist文件  
以下操作需要python环境  
使用[MacInfoPkg](https://github.com/acidanthera/MacInfoPkg/releases)生成SystemSerialNumber 和 MLB  
命令  
uuid随便在线生成个，作为SystemUUID  
mac address同样在线生成个，作为ROM（去掉 : 或者 -, 全部转换为大写）  
修改config.plist文件可以使用xcode（不要使用xcode11）或[ProperTree](https://github.com/corpnewt/ProperTree)~~  
#### 安装mac os
* 使用[etcher](https://www.balena.io/etcher/)将镜像写入u盘
* 插入u盘启动机器，选择install macOS Catalina
* 插入u盘启动机器，进入引导选择install macOS Catalina

#### 挂在EFI


### TODO
* 测试USB TYPE C


### 更新

### 参考资料
[使用OpenCore安装黑苹果](https://github.com/cattyhouse/oc-guide)  
[精解OpenCore](https://blog.daliansky.net/OpenCore-BootLoader.html)  
[使用OpenCore引导黑苹果](https://blog.xjn819.com/?p=543)  
[黑苹果入门教程](https://sleele.com/2019/07/14/gettingstartedtutorial/)  
