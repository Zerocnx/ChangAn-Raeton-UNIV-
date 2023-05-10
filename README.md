# 长安车机不完美破解思路

### 前言

> ​	各位工具箱的大佬，于我无关啊，莫名奇妙被点着名骂了，以前都是加了验证然后进群获取卡密，现在已经去掉验证放了。没验证了。
>
> ​	各位工具箱的大佬，于我无关啊，莫名奇妙被点着名骂了，以前都是加了验证然后进群获取卡密，现在已经去掉验证放了。没验证了。
>
> ​	各位工具箱的大佬，于我无关啊，莫名奇妙被点着名骂了，以前都是加了验证然后进群获取卡密，现在已经去掉验证放了。没验证了。
> 不收费啊 都是免费
> 不收费啊 都是免费
> 不收费啊 都是免费
> 工具箱之前都一直是免费，包括远程调试，3月份跟着55贴吧的教程研究出来教程，然后不完美破解可以了，然后都太多了开始写了第一版工具箱，后面找到一个adb工具箱的e语言源码，然后就更新了，一直也是免费，这里分享思路跟命令。然后可以写成bat文件，直接运行即可

### 思路 - 感谢以下作者分享出来的思路

> 易语言adb工具源码原作者：@Lc_Rose

> Cs55plus 贴吧破解思路作者：@时距曲线

> 自动解压apk思路：@长安小雕雕

> 感谢意思作者分享的文件提供的思路

###  流程

##### 1、准备工作

电脑一台
双USB数据线（电脑支持Type-c可以用手机线)
ADB工具箱（百度）

##### 2、车机开启USB调试与切换USB端口为ADB

拨号 *#*#888 密码：369875（不同车型不一样，具体百度）
工程模式，切换usb为adb模式(用完adb记得切换为U盘模式)

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml17048\wps1.png) 

然后 打开 原生 系统设置界面

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml17048\wps2.png)
最下面，狂点版本号，提示“已经是开发者调试模式"后按右上角的放大镜图标返回上级

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml17048\wps3.png)
高级设置，下面的“开发者选项”，找到USB调试，打开

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml17048\wps4.png) 

###  安装流程

##### 1、启动adb

解压 adb工具，然后打开文件夹，在地址栏直接输入CMD

```shell
adb devices   #查看设备列表
```

返回的如图才算读取到车机，不过不是说明有问题，请检查上面的步骤。

![image-20230510111131109](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230510111131109.png)

##### 2、解除车机分区验证

> 车机第一次弄的时候需要解除系统分区验证，不然无法挂载分区

```shell
adb root   #获取adb  root权限
adb disable-verity    #关闭分区验证
adb  reboot      #重启车机
```

如下图提示为成功，

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml17048\wps5.jpg)

##### 3、删除\VecentekApp.apk  （decore保护软件）

车机这个软件会检测推送进去的文件，然后有不对的会直接自动卸载掉

```shell
22款UNIT 名称不一样 是这个文件，所以命令也要自己修改一下。(区分大小写)
 /system/app/deCoreAppUser/deCoreAppUser.apk
 
车机重启后，输入
adb root   #获取adb  root权限
adb remount    #挂载分区，获得可写权限
adb shell     #进入shell  密码 adb36987
cd /system/app/VencentekApp/       #进入文件目录
rm -ri  VencentekApp.apk          #删除APK文，按 y 确定删除
exit       #退出shell模式
adb  reboot    #重启车机
```

如下图：

![image-20230510111432090](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230510111432090.png)

##### 4、安装APP - 普通安装

```shell
adb root   #获取adb  root权限
adb remount    #挂载分区，获得可写权限
adb push bili.apk /system/app   #上传文件到/system/app/目录下
adb reboot #重启车机
有应用商店的要在应用商店随便下载一个app，桌面才显示图标，没有的就要用别的软件打开
```

如图：

![image-20230510111701666](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230510111701666.png)

##### 5、替换原厂高德\其它第三方软件

```shell
#因为不是完美破解，所以自己需要注意system分区的空间
查看内存命令：进入Shell 模式    df -h  第一条查看自己的空间
#高德需要解压LIB文件，如何解压看第六条
```

```shell
#锐程PLUS 因为系统空间太少，所以必须删除原厂高德重启之后再进行更新
#UNIT的 原厂高德在 /System/priv-app/Ayto
adb root   #获取adb  root权限
adb remount    #挂载分区，获得可写权限
adb shell  #进入shell  密码 adb36987
cd /system/app #进入system/app目录
rm -rf AutoNavi #删除自带高德
adb reboot #重启车机
adb root   #获取adb  root权限
adb remount    #挂载分区，获得可写权限
adb push AutoNavi/. /system/app/AutoNavi/ #将工具箱解压LIB后的文件夹推送到System/app
adb reboot #重启车机
#重启后打开高德
```

如图：

![image-20230510112540191](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230510112540191.png)

##### 6、如何解压APK的lib

```shell
#当直接安装APK，点击图标闪退，无法打开的问题，则使用解压APK后推送文件夹的方式
```

> 1、打开 adb 工具文件 ，并在该文件夹中创建对应 apk 名称的文件夹（名称为英文，不要用中文就行)

```shell
#这里使用替换原厂高德为例子，所以我创建的文件夹名称为AutoNavi
```

![image-20230510113825544](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230510113825544.png)

> 2、下载公版的高德车机版（百度可下载），然后放到刚刚创建的AutoNavi文件夹中，并改名为AutoNavi.apk

这是下载好的

![image-20230510114015919](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230510114015919.png)

然后改名为AutoNavi

![image-20230510114041540](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230510114041540.png)

用解压软件打开这个APK文件，找到LIB文件夹，解压到文件中

![image-20230510114123852](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230510114123852.png)



![image-20230510114146674](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230510114146674.png)

然后进入lib文件夹，把里面armeabi-v7a  改成 arm

![image-20230510114227513](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230510114227513.png)

![image-20230510114255193](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230510114255193.png)

完整目录如下

![image-20230510114335901](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230510114335901.png)

然后打开cmd执行adb工具，地址栏输入CMD，然后直接回车即可

![image-20230510114420471](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230510114420471.png)

```shell
#执行以下命令
adb root #获取权限
adb remount #挂载分区可读写
adb push AutoNavi/. /system/app/AutoNavi/ #push整个文件夹到System/app/AutoNavi 目录（看CMD窗口中的结果提示是否完成)
adb reboot #重启车机
```

##### 7、如何修复图标

```shell
#仅支持有应用商店的车机，要在应用商店随便下个app
比如推送了解压lib后的bili文件夹到system/app/bili/
命令如下：
adb root #获取权限
adb remount #挂载分区可读写
adb shell #进入shell
cd /system/app  #进入/system/app目录
mv bili/bili.apk /system/app/  #移动apk文件到/system/app
mv bili.apk /system/app/bili/  #将apk文件移回去
reboot #重启车机
```



### 如何写工具

```shell
#下面来一个简单的工具实例，bat文件
@echo off
rem:定义主菜单
:MENU
color 0f
echo --------------------------------------------------------------
echo                   adb工具箱
echo --------------------------------------------------------------
echo  锐程车机破解工具箱_V1.0
echo  a.wifi 连接车机 
echo  1.查看车机是否连接                  
echo  2.删除原车机高德                     
echo  3.安装新版高德
echo  4.重启车机
echo  5.卸载
echo  0.退出
echo ---------------------                   
set /p Xz=输入命令选项：
if "%Xz%"=="a" goto connect
if "%Xz%"=="1" goto devices
if "%Xz%"=="2" goto rmautonavi
if "%Xz%"=="3" goto insautonavi
if "%Xz%"=="4" goto rreboot
if "%Xz%"=="5" goto un
if "%Xz%"=="6" goto ico
if "%Xz%"=="0" goto eexit

rem:WiFiADB功能
:connect
set /p input=输入车机IP地址：
adb connect %input%
TIMEOUT /T 5
adb devices
pause
goto MENU

rem:查看车机是否连接
:devices
adb devices
TIMEOUT /T 5
goto MENU

rem:卸载原车高德/unit是/system/priv-app
:rmautonavi
adb root
TIMEOUT /T 3
adb remount
TIMEOUT /T 3
echo adb36987|adb shell rm -rf /system/app/AutoNavi/
adb reboot
goto MENU

rem:安装高德或者第三方软件
:insautonavi
adb root
TIMEOUT /T 3
adb remount
TIMEOUT /T 3
adb push AutoNavi/. /system/app/AutoNavi/
adb reboot
echo 车机重启成功！
goto MENU

rem:删除功能
:un
set /p cc=要删除的文件夹名称：
echo adb36987|adb shell rm -rf /system/app/%cc%
echo %cc%卸载成功，请重启车机
goto MNEU

rem:修复桌面没有图标，仅支持有应用商店的车机，要在应用商店随便下个app
:ico
ser /p ii=要修复图标的app名称(英文):
echo adb36987|adb shell mv /system/app/%ii%/%ii%.apk /system/app/
echo 第一步修复完成！
echo adb36987|adb shell mv /system/app/%ii%.apk /system/app/%ii%/%ii%.apk
echo 第二部修复完成！车机即将重启！
TIMEOUT /T 3
adb reboot
goto MENU

:rreboot
adb reboot
goto MENU

:eexit
exit

```




