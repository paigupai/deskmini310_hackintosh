
# deskmini310_hackintosh
猿でもわかるhackintosh（MACOS 10.15版)
本教程使用xjn大神已打包好的10.15.1镜像，是基于OpenCore来引导黑苹果，教程仅供参考

### 配置

| 配置 | 型号 |
|:-----------|:------------:|
| CPU       |     i3 9100     |
| 散热       |     穷，用的原装     |
| 内存     |    G.Skill F4-2400C16D-16GRS    |
| ssd       |     WD Blue SN550 NVMe WDS500G2B0C     |
| 网卡         |      BCM94360CS2      |

### 状况

* DP: 完美，可以dp转hdmi同样没问题
* hdmi: 可双屏，但是不能单hdmi，会卡引导
* 睡眠: 完美
* 蓝牙/WIFI: OK
* 有线网卡: OK
* 声卡: OK
* USB: 键鼠usb等ok，但是插入TP LINK Archer T2UH无反应
* USB TYPE C: 未测试

### BIOS设置

* Load UEFI Defaults（恢复出厂设置）
* Advanced
  * CPU Configuration
    * CFG Lock: Disabled
  * Chipset Configuration
    * Onboard HD Audio: Enabled
  * USB Configuration
    * XHCI Hand-off：Enabled
  * ~~Super IO Configuration, Serial Port, Disabled（BIOS 4.2中Super IO Configuration被删除了，无法修改,无视本项）~~
* Security
  * Secure Boot：Disabled(by default)
* Boot
  * CSM：Disabled

### 安装
镜像下载请参考[xjn的超级小白教程](https://blog.xjn819.com/?p=7#comment-464)最新为10.15.1
直接下载镜像，写入到u盘即可，如果嫌百度网盘慢，可以冲3块钱用[速盘](https://www.speedpan.com/)
※注意这个教程中安装的是基于OpenCore的引导，而非clover，所有基于clover引导的修改都是不行的，如果之前安装过clover黑苹果🍎，是无法直接使用的（[参考](https://blog.daliansky.net/OpenCore-BootLoader.html)）
#### 修改序列号3码
~~无视
不影响使用，不介意的人可以跳过，可在windows环境修改
修改序列号需要编辑config.plist文件
以下操作需要python环境
使用[MacInfoPkg](https://github.com/acidanthera/MacInfoPkg/releases)生成SystemSerialNumber 和 MLB
uuid随便在线生成个，作为SystemUUID
mac address同样在线生成个，作为ROM（去掉 : 或者 -, 全部转换为大写）
修改config.plist文件可以使用xcode（不要使用xcode11）或[ProperTree](https://github.com/corpnewt/ProperTree)~~
#### 安装mac os
* 使用[etcher](https://www.balena.io/etcher/)将镜像写入u盘
* 插入u盘启动机器，选择install macOS Catalina，打开磁盘工具，抹掉内置硬盘，方案选择“GUID 分区图”，格式选择“APFS”（推荐）
* 安装macOS，安装到刚才抹掉的硬盘，安装过程会重启1-3次，重启之后，选择接着安装macOS
* 安装成功后，会进入macOS初期设定，进入系统测试无问题，就是安装成功了

#### 挂载EFI
##### 模拟NVRAM
* 此时macOS虽然安装成功，但开机需要用usb来引导开机，需要把usb引导开机改为硬盘引导开机
* 安装clover configurator，通过挂载分区，来打开usb内的efi文件夹内的LogoutHook文件夹，将LogoutHook.command放入文档目录（/Users/你的用户名/Documents/）下
* 打开终端，执行以下命令:
```
sudo defaults write com.apple.loginwindow LogoutHook /Users/你的用户名/Documents/LogoutHook/LogoutHook.command
```
* 输入密码（密码打进去不会显示）
* 重启后，你会在/EFI/下找到nvram.plist，代表已经成功模拟了

##### 挂载EFI
* 使用clover configurator打开内置硬盘的efi分区，将刚才生成的nvram.plist文件放到跟efi文件夹相同的路径下
* 把usb内的efi文件夹的BOOT文件夹和OC文件夹复制到内置硬盘的efi分区下，打开系统偏好设置---启动磁盘，选择内置硬盘为默认启动的启动磁盘
* 拔掉u盘，重启，即可，默认启动项为内置硬盘名

[参考：使用OpenCore引导黑苹果 3.0 OpenCore 完善](https://blog.xjn819.com/?p=543)

### 推荐软件
[Carbon Copy Cloner](https://bombich.com/ja)
[AppCleaner](https://freemacsoft.net/appcleaner/)

### TODO
* 测试USB TYPE C


### 更新
* 2020.1.22 新规完成
* 2020.2.1 成功更新10.15.3，无异常
![avatar](https://github.com/paigupai/deskmini310_hackintosh/raw/master/image/10.15.3.png)

### 参考资料
[使用OpenCore安装黑苹果](https://github.com/cattyhouse/oc-guide)  
[精解OpenCore](https://blog.daliansky.net/OpenCore-BootLoader.html)  
[使用OpenCore引导黑苹果](https://blog.xjn819.com/?p=543)  
[黑苹果入门教程](https://sleele.com/2019/07/14/gettingstartedtutorial/)  
