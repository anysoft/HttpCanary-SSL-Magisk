## HttpCanary Magisk Module
- [x] SSL

### Tested on
- [x] Android 11
- [x] Android 12.1



# 一些说明

当前各个版本中，在Android 12中无法使用`HttpCnary Premium`版本,只能使用`HttpCnary`(激活高级功能)版本了，两者有一定差异。

## 版本说明

官方有两个包

1. com.guoshi.httpcanary
   - [HttpCanary - Google Play](https://play.google.com/store/apps/details?id=com.guoshi.httpcanary)
2. com.guoshi.httpcanary.premium
   - Play 可能下架了

针对`crack`流传比较广的是`9.2.8.1`版本,应该是基于`2.8.1`版本修改的，支持注入功能。然后就是目前`HttpCanary` 和 `HttpCanary Premium` 的`3.3.6`，其中`HttpCanary Premium` 有内嵌Google Play crack的也有剔除了Google Play的版本(大小分别是18MB和5MB)

在此基础上还有HttpCanary 3.0+版本制作的 HttpCanary 高级版 crack，有些直接把UI全改了，甚至包名也改了，出了个所谓重置版，这里就不多描述。

## 兼容问题
​		此处主要讲一下Android版本的兼容问题。
首先原版到目前测试Android12都正常支持的，修改版中 `HttpCanary Premium` 的`3.3.6` 内嵌Google认证的 18MB的版本在Android12上会闪退(不确定所有Android12 都闪退)。
​		所有包如下：存放backups目录，如果你有其他包可以通过pull request提交上来。

### Premium(老鹰图标)
- [HttpCanary_v3.3.6_Premium_Crack_NoUpdate.](backups/HttpCanary_v3.3.6_Premium_Crack_NoUpdate.apk)
  - 该版本Android 12可以安装，但是抓包无法激活VPN，可以自行尝试

- [HttpCanary_v3.3.6_Premium_GooglePlay_Crack](backups/HttpCanary_v3.3.6_Premium_GooglePlay_Crack.apk)
  - 此版本Android 12上闪退，自行测试


### 免费版(黄蜂图标，激活高级功能)
- [HttpCanary_v2.8.1 Crack_NoUpdate](backups/HttpCanary_v2.8.1_Premium_Crack_NoUpdate.apk)
  - 此版本Android 12 可以正常使用，高级功能已激活

- [HttpCanary_v3.3.6_repackaged](backups/HttpCanary_v3.3.6_repackaged.apk)
  - 此版本Android 12 可以正常使用，高级功能已激活
  - 此版本修改者把UI换成蓝色的了，做了微调

- [HttpCanary_v3.3.6_repackaged_pure](backups/HttpCanary_v3.3.6_repackaged_pure.apk)
  - 此版本Android 12 可以正常使用，高级功能已激活
  - 此版本修改者把UI也换色了，且极度精简了，具体自行测试，APK签名也变了

- [HttpCanary_v4.8.6_Mod](backups/HttpCanary_v4.8.6_Mod.apk)
  - 此版本Android 12 可以正常使用，高级功能已激活
  - 此版本修改者把图标/名称/包名(`com.httpcanary.pro`)都改了，且抓包列表不显示被抓包的程序图标






## 关于证书
​		HttpCanary 使用的自签证书应该是本地生成的(每次安装后都会不一样)，这样做可以确保设备的网络数据安全，因为使用固定的/别人提供的证书本地网络数据是存在被劫持的风险！(当然只是说存在风险情况而已)。

​		如果您没有**Root**手机，也无需把证书迁移到**系统证书**下，那么直接安装APP后把证书导出到sdcard上再到Android系统`设置`里导入ca证书即可。

​		如果您**Root**手机了，可以直接使用本模块自动安装APP且配置系统证书，当然我们更加希望您能自己在本模块的基础上简单diy下，制作属于自己独有证书的模块包。

Diy方式：
- 手动安装`HttpCanary`

- 在`HttpCanary`内导出证书为`System Trusted(.0)`文件，会保存在'/sdcard/HttpCanary/certs文件夹内'，用它替换模块内`system\etc\security\cacerts` 文件夹下的`87bc3517.0`

- 进入`/data/data/com.guoshi.httpcanary` 或者 `/data/data/com.guoshi.httpcanary.premium`下`cache`目录将内部文件复制出来替换模块下`data\data\com.guoshi.httpcanary.premium\cache`目录文件，然后压缩模块即完成了属于自己的证书的模块

- 最后刷入自己修改后的模块重启手机即可


### FAQ
1. Q：有时候刷入模块安装后APP内还是显示证书未安装
A： 因为APK内证书和系统内置证书不一致导致的，你可以导出`System Trusted(.0)` 用它替换模块内`system\etc\security\cacerts`后重启手机即可。(`HttpCanary`清除数据后重启`HttpCanary`会生成新的证书文件，所以非必要不要清除数据，如果清除数据了，那么重新刷入模块重启手机，或者导出证书`87bc3517.0`替换模块内该文件重启手机)



