# 拒绝TeamViewer，跨平台远程控制

## 为什么要跨平台？

因为工作原因，手上系统有Andoird，iOS，MacOS，Linux，Windows，靠平台自带远程工具无法满足要求。

跨平台远程控制软件有这么几款：

* TeamViewer：非商用免费，支持内网穿透，不稳定，对版本有要求
* Splashtop：局域网免费，跨网段/穿透收费
* VNC：免费，不支持内网穿透
* 向日葵：个人觉得不好用，Pass

## 为什么放弃TeamViewer

TeamViewer局域网卡顿，设备时不时离线，甚至双方版本不一致也不让用。

于是我开始寻找替代品，最后找到VNC，免费，跨网段不收费，且稳定流畅，MacOS天生支持。

问题来了，怎么解决内网穿透的问题？

答案就是虚拟局域网，将多台设备接入同一个虚拟局域网，这样不仅能方便控制，而且共享什么的也很方便。

经过多番尝试，最终选择Zero-Tier，同样跨平台，而且不怕IP变动。

为了内网穿透，你需要准备至少一台拥有公网IP的设备。（比如阿里云服务器）

使用方法：

1. 官网注册账号登录，新建一个通道，获得ID，选择局域网IP段。
2. 下载软件，运行
3. 加入通道
4. 官网同意加入申请，填写备注。

现在，你所有的设备都在同一个局域网VPN中。VNC输入后台显示的IP即可。

不过Splashtop依旧不会这么认为，所以还是只能用VNC。TeamViewer就作为备用吧。

by [@雨声敲敲](www.weibo.com/rainssong)

2020-01-11

---

## 更多阅读：

[知乎专栏——来点技能点 https://zhuanlan.zhihu.com/SkillPoint](https://zhuanlan.zhihu.com/SkillPoin)——各类计算机骚操作

[智能家居排雷贴 https://zhuanlan.zhihu.com/p/87595668](https://zhuanlan.zhihu.com/p/87595668)——实实在在的生活品质

[知乎专栏——随机漫步的玩家 https://zhuanlan.zhihu.com/iwander](https://zhuanlan.zhihu.com/iwander)——点订阅，看更多好玩意

[极米H3投影评测 http://rainssong.github.io/#/posts/1](http://rainssong.github.io/#/posts/1)

[极米投影官方店 https://j.youzan.com/5ZMTjY](https://j.youzan.com/5ZMTjY)——先买200优惠券，可兑换3D眼镜 
