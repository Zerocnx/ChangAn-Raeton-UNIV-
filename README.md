# ChangAn-Raeton-UNIV
长安锐程Plus/Univ车机安装第三方
## 前言
>>只提供思路与教程，中间车机出现的一切后果与本人无关，由操作人自己负责。没有任何费用。</br>
>>只提供思路与教程，中间车机出现的一切后果与本人无关，由操作人自己负责。没有任何费用。</br>
>>只提供思路与教程，中间车机出现的一切后果与本人无关，由操作人自己负责。没有任何费用。</br>
>>灵感来源于：https://tieba.baidu.com/p/7744288073#noExistHash</br>
>>电脑要安装adb驱动，提供一个，不保证能用。
# 一、车机开机USB调试
>>进入工程模式，切换usb为adb模式(用完adb记得切换为U盘模式)</br>
>>然后  打开 原生 系统设置界面最下面，狂点版本号，提示“已经是开发者调试模式"后按右上角的放大镜图标返回上级高级设置，
    下面的“开发者选项”，找到USB调试，打开
```shell
拨号 *#*#888    密码：369875   #进入工程模式
```
# 二、打开 ADB工具，安装第三方软件
使用数据线将电脑与车机连接起来，在adb文件夹中运行CMD
```shell
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
```
.apk文件放在adb的目录下，可以少输一点命令
 记得安装完后要把usb模式切换成u盘模式

# 三、adb 驱动/工具/软件下载
	ADB工具与软件下载：https://wwi.lanzoup.com/b00qsf1xe#6666
    OPPo可以用这个，CarLink_USB_7.0和闪退用这个.apk，然后USB 没问题，要断开蓝牙连接。
     Carlink：非常感谢软件提供作者  Xander（酷安：斩月灬太保），QQ群：487558648。感谢老哥修改carlink 可用。
#四、UNIV老哥的车机（酷安：卖萌三公主）
```shell

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
```
#五、图片
Carlink  oppo（目前测试只有USB，全屏）


百度carlife（USB跟wifi都可以，不是全屏）


重启后桌面显示第三方软件
