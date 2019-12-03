title: "简易赛车的AI写法"
date: 2015-06-30 02:08 
tags: 
- AS3
- GameDevelop
- AI
categories:
- GameDevelop
---

wonderfl上有一个神奇的3D赛车游戏，只有短短的500行代码就实现了随机生成赛道数木障碍物，AI对手，视野控制等等功能。今天看了一下它的AI部分的源码，感觉相当秒。这里分享一下。游戏地址：http://wonderfl.net/c/njap

    public function getAutoKey(w:World):uint
    {
        //上 下 左 右 手刹，默认前进
        var key:uint = 0xF0000;
        //p：车座标，cp：目标点坐标，ofp：需要的位移量
        var p:Point = new Point(qobject.x, qobject.y), cp:Point = w.course[_targetIndex], ofp:Point = cp.subtract(p);
        //目标距离
        var d:Number = Point.distance(p, cp);
        //如果方向正确且快到目标点则更新目标点
        if (d < 10 + speed / 10 * proactiveRate || (cp.x * p.y) - (cp.y * p.x) > 0)
            _targetIndex = ++_targetIndex % w.course.length;
        //夹角公式，如果夹角大于0.12则转弯
        if (Math.acos((ofp.x * _front.x + ofp.y * _front.y) / (ofp.length * _front.length)) > 0.12)
            key |= (ofp.x * _front.y - ofp.y * _front.x > 0) ? 0x00F00 : 0x000F0;
        //前进受阻严重则倒车
        if (!_backMode && speed < 2 && ++_stress > 80)
            _backMode = true;
        //受阻减少则恢复
        else if (_backMode && --_stress <= 0)
            _backMode = false;
        //倒车时前后左右相反
        if (_backMode)
            key ^= 0xFFFF0;
        //弯度、速度、距离满足条件时飘移
        if (speed > 7 && w.tightness[_targetIndex] > 1 && d < 20)
            key |= 0x0000F;
        return key;
    }

有时候只用if实现AI已经足够