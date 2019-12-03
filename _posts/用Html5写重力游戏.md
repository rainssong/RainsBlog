title: "用Html5写重力游戏"
date: 2015-05-11 02:08 
tags: 
- GameDevelop
- Egret
- Html5
categories:
- GameDevelop
---

之前用Egret把我的游戏移植为Html5小游戏。游戏地址：http://finalflight.sinaapp.com/
网上对于Html5重力游戏的资料有点零散，说的也不是很清楚，这里总结一下。
首先说一下三个相关事件：
DeviceMotionEvent——设备的加速度信息
DeviceOrientationEvent——设备的角度信息
MozOrientationEvent——火狐浏览器的角度信息

其实通常情况下用DeviceOrientationEvent即可完成设备倾斜度的判断，怎奈Html5标准不统一的问题，还要想办法做一下兼容。

	public onOrientation(e):void
    {
        //未测试安卓，估计也要取反，见onMotion函数
        //将Moz参数转换为一般参数
        if (!e.gamma && !e.beta) 
        {
            e.beta = (e.x * (180 / Math.PI)); //转换成角度值
            e.gamma = (e.y * (180 / Math.PI)); //转换成角度值,
            e.alpha = (e.z * (180 / Math.PI)); //转换成角度值
        }
         //沿X旋转的角度
        this.gamma = e.gamma;
         //沿Y旋转的角度
        this.beta = e.beta;
        //沿Z旋转的角度
        this.alpha = e.alpha;
    }

如果你的游戏用到了重力加速度，就这么写

	public onMotion(e):void
    {
         //如果是安卓则取反
        var reverseRate:number=<number>(SystemManager.isAndroid?-1:1);
        this.x = e.accelerationIncludingGravity.x*reverseRate
        this.y = -e.accelerationIncludingGravity.y*reverseRate
        this.z = e.accelerationIncludingGravity.z*reverseRate
    }

如果只用到加速度，这么写：

	public onMotion(e):void
    {
        var reverseRate:number=<number>(SystemManager.isAndroid?-1:1);
        this.x = e.acceleration.x*reverseRate
        this.y = -e.acceleration.y*reverseRate
        this.z = e.acceleration.z*reverseRate
    }

用重力加速度更能捕捉玩家的动作，倾斜度的话比较好理解控制也更佳僵硬和精确一些。

然后将检测到的参数封装成一个单例类，游戏即可随时调用结果。否则传感器初始化会造成卡顿影响体验。

另外，手机会自动关灯，所以你要设计一些功能使得玩家隔段时间（建议20秒以内）就去点击一下屏幕。