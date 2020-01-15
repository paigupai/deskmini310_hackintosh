# deskmini310_hackintosh
猿でもわかるhackintosh（MACOS 10.15版)  
本教程仅供参考

### 配置

### 状况

### 安装
[大佬的超级小白教程](https://blog.xjn819.com/?p=7#comment-464)最新为10.15.1  
直接下载镜像，写入到u盘即可，如果嫌百度网盘慢，可以冲3块钱用[速盘](https://www.speedpan.com/)  
※注意这个教程中安装的是基于OpenCore的引导，而非clover，所有基于clover引导的修改都是不行的，如果之前安装过clover黑苹果🍎，是无法直接使用的（[参考](https://blog.daliansky.net/OpenCore-BootLoader.html)）  
#### 修改序列号3码
直接套用别人的EFI会导致序列号3码重复，iMessage，FaceTime，iCloud会被拉黑名单无法使用，不介意的人可以跳过这部分。  
修改序列号需要编辑config.plist文件  
以下操作需要python环境  
使用[MacInfoPkg](https://github.com/acidanthera/MacInfoPkg/releases)生成SystemSerialNumber 和 MLB  
uuid随便在线生成个，作为SystemUUID  
mac address同样在线生成个，作为ROM（去掉 : 或者 -, 全部转换为大写）  
修改config.plist文件可以使用xcode（不要使用xcode11）或[ProperTree](https://github.com/corpnewt/ProperTree)  ([图标美化版](http://bbs.pcbeta.com/viewthread-1832755-1-1.html))
### TODO



### 参考资料
[使用OpenCore安装黑苹果](https://github.com/cattyhouse/oc-guide)  
[精解OpenCore](https://blog.daliansky.net/OpenCore-BootLoader.html)
[使用OpenCore引导黑苹果](https://blog.xjn819.com/?p=543)
