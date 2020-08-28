# 打通Android、Windows、MacOS、iOS文件共享

家里设备一多，不共享就不行，总不能用QQ传文件吧。还好Windows，MacOS和iOS对smb的支持都挺完整，只有Android比较困难，如果你的安卓总是访问不了共享，可以拉到最后。

## Windows共享

文件夹右键属性-共享-高级共享，如果安卓无法访问，尝试以下几项：

1. 文件夹右键属性-共享-高级共享-权限-添加-Everyone
2. 控制面板\所有控制面板项\网络和共享中心\高级共享设置-无密码的保护共享，这一步是无奈之举，我发现很多安卓设备根本就不支持密码smb
3. 控制面板\所有控制面板项\程序和功能-启用或关闭Windows功能-勾上SMB1.0共享支持

访问时，直接在文件夹路径里输入IP如：\\192.168.0.10

除了smb之外，偶尔我也会用EveryThing来开启ftp和http文件服务，一键搞定真的太方便了。。。

## MacOS共享

系统设置-共享-添加文件夹

[官方教程 https://support.apple.com/zh-cn/HT204445](https://support.apple.com/zh-cn/HT204445)

## iOS共享

iOS13后文件App自带局域网访问功能，不过有些BUG，可以下一个FileExplorer。

## Android

ES文件浏览器可作为客户端，但是安卓对SMB支持不好，但可以启用ftp。

## 其它跨平台工具

利用ResilioSync可以建立一个共享专用文件夹，自动只要扫码即可参与到共享中，类似OneDrive不过没有云存储。

如果只是像微信那样快速传递少量文件，可以使用AirDorid。优点是还有文件管理、Web版、远程操控，缺点是Win版软件启动慢了些。

by [@雨声敲敲](www.weibo.com/rainssong)
2020-01-11

----

## 更多阅读：

[智能家居排雷贴 https://zhuanlan.zhihu.com/p/87595668](https://zhuanlan.zhihu.com/p/87595668)

[知乎专栏——随机漫步的玩家 https://zhuanlan.zhihu.com/iwander](https://zhuanlan.zhihu.com/iwander)

[极米H3评测 http://rainssong.github.io/#/posts/1](http://rainssong.github.io/#/posts/1)

[极米官方店 https://j.youzan.com/5ZMTjY](https://j.youzan.com/5ZMTjY)——先买200优惠券，可兑换3D眼镜 

