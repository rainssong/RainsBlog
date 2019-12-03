title: "Air中File类获取地址的研究 "
date: 2012-08-30 00:35
tags: 
- AS3
- Air
categories:
- AS3
---

Adobe帮助文档中说得比较松散和含糊，这是自己实验得到的结果 

File.applicationDirectory 

	url = "app:/"
	nativePath(IOS) = "/var/mobile/Applications/6D8923A6-2B86-4C46-AE7A-7B6AFB349DDE/[app name].app"//此文件夹是压缩包，只读
	nativePath(WIN) = [绝对路径]
	nativePath(Android) = "" 

注意： 不要在应用程序目录（AIR 应用程序的安装位置）中添加或删除内容。否则会损坏 AIR 应用程序，应用程序签名也将失效。AIR 默认不允许写入应用程序目录，因为该目录并非对所有操作系统上的所有用户帐户均为可写目录 

File.applicationStorageDirectory 

	url = "app-storage:/"
	nativePath(IOS) = "/var/mobile/Applications/6D8923A6-2B86-4C46-AE7A-7B6AFB349DDE/Library/Application Support/[app id]/Local Store"//可写
	nativePath(WIN) = "C:\Users\[UserName]\AppData\Roaming\[App Id]\Local Store"
	nativePath(Android) = "/data/data/air.[appid]/ [appid] /Local Store"


File.documentsDirectory 

	url = "file:///var/mobile/Applications/6D8923A6-2B86-4C46-AE7A-7B6AFB349DDE/Documents"//可写
	url (Android)= " file:///storage/emulated/0"
	nativePath(IOS)= "/var/mobile/Applications/6D8923A6-2B86-4C46-AE7A-7B6AFB349DDE/Documents"
	nativePath(WIN)= "d:\Documents\[UserName]\My Documents"
	nativePath(Android)= "/storage/emulated/0"


File.desktopDirectory

	url = "file:///var/mobile/Applications/6D8923A6-2B86-4C46-AE7A-7B6AFB349DDE/Desktop"
	nativePath(IOS)= "/var/mobile/Applications/6D8923A6-2B86-4C46-AE7A-7B6AFB349DDE/Desktop"//可写
	nativePath(WIN)= "d:\Documents\[UserName]\Desktop"


File.userDirectory 

	url = "file:///var/mobile/Applications/6D8923A6-2B86-4C46-AE7A-7B6AFB349DDE"
	url(Android) = "file:///storage/emulated/0"
	nativePath(IOS)= "/var/mobile/Applications/6D8923A6-2B86-4C46-AE7A-7B6AFB349DDE"//可写
	nativePath(WIN)= "C:\Users\[UserName]"
	nativePath(Android)= " /storage/emulated/0"

File.cacheDirectory 

	nativePath(Andorid) = /data/data/air. [appid] /cache
	url( Andorid ) = file:///data/data/air. [appid] /cache

由于AIR限制太多，实际操作中最好使用类似new File(File.applicationDirectory.resolvePath("sb.jpg").nativePath)的方式来获取File对象，保证最大权限


作者：Rainssong 
来源：http://blog.sina.com.cn/rainssong 
转载请保留作者信息 