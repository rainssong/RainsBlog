title: Air开发iOS应用的适配
date: 2012-09-17 11:15 
tags: 
- AS3
- Air
- iOS
categories:
- AS3
---

一共有三个方案。

1.告诉IOS本应用不支持高分。
只要调整应用配置的分辨率选项为standard。 
（IOS下修改application.xml：<requestedDisplayResolution>standard</requestedDisplayResolution>）
此情况下，IOS会主动将分辨率调整至标准。使用此法应用的效率较高。

2.告诉App主动放大至全屏。
调整应用配置的分辨率选项为high。
（ IOS下修改application.xml ：<requestedDisplayResolution>high</requestedDisplayResolution>）
另外要设置
stage.scaleMode = StageScaleMode.SHOW_ALL;（由于默认就是SHOW_ALL，不设亦可。不过为了表明你要缩放的决心，最好是写上）

3.使用自适屏技术。
设stage.scaleMode = StageScaleMode.NO_SCALE; 
侦听舞台的Resize事件 
并对UI层和内容层分开处理