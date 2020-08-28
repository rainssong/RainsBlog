# Unity动态执行脚本的尝试

项目需要用到解释器，于是各种苦找，找完还要对比。

## 动态执行JS

1. [Jurassic](https://github.com/paulbartrum/jurassic)，登陆UnityAssestStore，很久没更新了，亲测可用，绑定麻烦，用起来不是很爽。
2. jint，jint效率比Jurassic差，似乎不支持多方法，优点是一直在更新。
3. CleanScript， 微软出的，弄半天没发现如何正确导入Unity
4. JSBinding，登陆UnityAssestStore，已 下架，作者放弃更新

## 动态执行C#

1. UniScript，基于SlowSharp搞的，可以在Play状态下绑定Behavior或者重载类，修改也是即时生效，不需要做准备工作，即插即用，能绕过苹果的机制。
2. madlag/unity-csharp-interpreter，一套反射的方案，亲测可行，原理似乎是动态编译？调用起来有些麻烦。
3. C#Light，模拟C#的脚本语言，没有文档，作者弃坑，效率不行。

## 动态执行Lua

1. ulua，试了一下配置很麻烦
2. xlua，腾讯出的，自动绑定，相当方便。但我始终不喜欢lua，语法太死了。

## 效率测试

10万次加法,计算所用时间

*. jint 800ms
*. jurassic 46ms\~100ms
*. xlua 0ms\~16ms
*. UniScript 16ms\~47ms
*. C#Light 550ms

## 结论

*. UniScript最大的优势是绕过了编译，用于调试或者二次开发、扩展会方便。
*. xlua，看下来依旧是最好用的动态方案。
*. Jurassic，效率和方便程度都不行，暂无需求。
