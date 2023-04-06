# ChangAn-Raeton Plus-UNIV-UNIT
长安锐程Plus/Univ车机破解，安装第三方软件
## 前言
>>只提供思路与教程，中间车机出现的一切后果与本人无关，由操作人自己负责。没有任何费用。</br>
>>只提供思路与教程，中间车机出现的一切后果与本人无关，由操作人自己负责。没有任何费用。</br>
>>只提供思路与教程，中间车机出现的一切后果与本人无关，由操作人自己负责。没有任何费用。</br>
>>灵感来源于：https://tieba.baidu.com/p/7744288073#noExistHash</br>
>>电脑要安装adb驱动，提供一个，不保证能用。

### 腾讯文档教程已经更新，扫码或点击连接查看
[![](https://www.yongtao.org/content/uploadfile/202304/thum-3f411680744071.png)](https://www.yongtao.org/content/uploadfile/202304/3f411680744071.png)

### 在线文档请查看：[【腾讯文档】车机破解_锐程plus_UNIV_UNIT_v2.3](https://docs.qq.com/doc/DWldXbXZUa0JzRVpL)

# 前言
## 只提供思路与教程，中间车机出现的一切后果与本人无关，由操作人自己负责。没有任何费用。
## 只提供思路与教程，中间车机出现的一切后果与本人无关，由操作人自己负责。没有任何费用。
## 只提供思路与教程，中间车机出现的一切后果与本人无关，由操作人自己负责。没有任何费用。
## 灵感来源于：https://tieba.baidu.com/p/7744288073#noExistHash
## 电脑要安装adb驱动，提供一个，不保证能用。
#### 一、车机开机USB调试
    		拨号 *#*#888    密码：369875  
		进入工程模式，切换usb为adb模式(用完adb记得切换为U盘模式)
   		 然后  打开 原生 系统设置界面>最下面，狂点版本号，提示“已经是开发者调试模式"后按右上角的放大镜图标返回上级>高级设置，
		下面的“开发者选项”，找到USB调试，打开
#### 二、打开 ADB工具，安装第三方软件
		使用数据线将电脑与车机连接起来，在adb文件夹中运行CMD
		adb root     #切换adb ROOT权限
		adb remount  #重新挂载分区（挂载失败：先输入 adb disable-verity ，然后  adb reboot重启车机后再挂载)
		adb pull /system/app D:\bak\    #备份 /system/app 下的所有文件
		adb pull /system/priv-app  D:\bak\priv-app     #备份 /system/priv-app 下的所有文件
		adb shell #进入shell模式，密码：adb36987
		su #切换到root #（如果后面是#,则无须切换)
		cd /system/app/VecentekApp/  #进入decore目录
		rm -rf VecentekApp.apk  #删除decore
		exit  #退出shell模式
		adb push *.apk /system/app #上传apk文件到车机系统目录
		abd reboot #重启车机
		.apk文件放在adb的目录下，可以少输一点命令
		记得安装完后要把usb模式切换成u盘模式
		
### 三、adb 驱动/工具/软件下载
	ADB工具与软件下载：https://wwi.lanzoup.com/b00qsf1xe#6666
		OPPo可以用这个，CarLink_USB_7.0和闪退用这个.apk，然后USB 没问题，要断开蓝牙连接。
		 Carlink：非常感谢软件提供作者  Xander（酷安：斩月灬太保），QQ群：487558648。感谢老哥修改carlink 可用。

### 四、UNIV老哥的车机（酷安：卖萌三公主）
		adb version #帮助信息
		adb root #获取 root (仅第一次使用)
		adb disable-verity #关闭检测功能(仅第一次使用)
		adb reboot #重启(仅第一次使用)
		adb root #获取 root 权限 
		adb remount#挂载系统读写
		#安装APP/提取
		#(提取应用)：adb pull /system/app/VecentekApp D:\666    
		#备份VecentekApp到C盘666文件夹下
		#删除保护软件(仅需一次)
		adb shell #进去adb shell密码：adb36987
		ls /system/app  #查看系统安装包
		cd /system/app/VecentekApp/ #进入保护app目录
		rm -ri VecentekApp.apk #删除保护软件(输入y回车确认)
		exit #退出 shell
		adb reboot #重启
		#(安装应用)：
		adb push C:\666\newApp.apk /system/
		#安装C盘新软件到system/app(软件名不能中文)
		adb reboot #重启车机

# 五、UNI-T车机保护软件
		22款UNIT 名称不一样 是这个文件，所以命令也要自己修改一下。
		 /system/app/deCoreAppUser/deCoreAppUser.apk
		 是这个文件，所以自己注意

# 六、安装亿联/高德共存7.0（其它第三方这样一样解压lib后推送到车机目录）
### 请注意自己车机内存来安装软件，小心司机
		查看内存命令：进入Shell 模式    df -h  查看自己的空间
		下载网盘里面的 <yl配合小白圈使用.zip>
		解压到adb目录下
[![](https://www.yongtao.org/content/uploadfile/202304/thum-9da91680744422.png)](https://www.yongtao.org/content/uploadfile/202304/9da91680744422.png)

		打开adb 工具
		输入以下命令
		adb root #获取root权限
		adb remount #挂载分区可写
		adb push yl/. /system/app/yl #安装yl
		adb reboot #重启车机
		亿联安装完桌面可能不显示图标，需要配合小白圈使用，目前测试 安卓/苹果 都有对应亿联APP可投屏

#### 安装完成后
[![](https://www.yongtao.org/content/uploadfile/202304/thum-a07a1680744494.png)](https://www.yongtao.org/content/uploadfile/202304/a07a1680744494.png)
#### 界面如下：
##### 苹果：
[![](https://www.yongtao.org/content/uploadfile/202304/thum-e10a1680744526.jpg)](https://www.yongtao.org/content/uploadfile/202304/e10a1680744526.jpg)
[![](https://www.yongtao.org/content/uploadfile/202304/thum-f79b1680744548.jpg)](https://www.yongtao.org/content/uploadfile/202304/f79b1680744548.jpg)
##### 安卓：
##### 这是oppo自带的车联，使用亿联软件的话界面跟苹果差不多
[![](https://www.yongtao.org/content/uploadfile/202304/thum-3bb91680744571.jpg)](https://www.yongtao.org/content/uploadfile/202304/3bb91680744571.jpg)

### 七、图片
	Carlink  oppo（目前测试只有USB，全屏）
[![](https://www.yongtao.org/content/uploadfile/202303/thum-5dfe1678341575.png)](https://www.yongtao.org/content/uploadfile/202303/5dfe1678341575.png)

	百度carlife（USB跟wifi都可以，不是全屏）
[![](https://www.yongtao.org/content/uploadfile/202303/thum-2d801678341605.png)](https://www.yongtao.org/content/uploadfile/202303/2d801678341605.png)

	重启后桌面显示第三方软件
[![](https://www.yongtao.org/content/uploadfile/202303/thum-c4fd1678341638.png)](https://www.yongtao.org/content/uploadfile/202303/c4fd1678341638.png)
