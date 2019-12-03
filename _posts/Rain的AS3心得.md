title: Rain的AS3心得 
date: 2013-11-12 16:37 
tags: 
- AS3
- Array
categories:
- AS3
---

理论篇：
· 用Vector存基础类型，用Array存复杂类型。
· 优先考虑代码可读性，计算量大时才考虑效率
· 勿滥用设计模式，设计模式是方法，不是目的。
· 需要复用的类要尽量保证独立性——避免主动调用外部类。它与外部的通信通过接口（函数和公有变量）和事件来完成。
· 使用事件总线EventBus负责接受和处理全局事件（eventDispatcher单例），可以轻松实现MVC。
· 资源用静态类管理。
· 每个类都实现destroy接口，用以删除所有引用和内部侦听器。.
· 会重复使用的特定数值/字符串，使用静态常量来存储，可以减少很多麻烦。
· 包名分清楚分细，不是极度相似的类不要重名，避免冲突和误调

技巧篇:

· 快速创建Vector的方法如下：new [1,2,3,4,5,6,7]
· 优先使用scrollRect而非mask
· 用单例管理类来获取单例。既减少了代码量，又使得类不受单例所限

	public static function getSingleton(Type:Class):*  
	{
		_dictionary[Type] ||= new Type();
		return _dictionary[Type] as Type;
	}

· 对于视图类，可以侦听REMOVED_FROM_STAGE事件后调用destroy，实现自动销毁
· 对于判断Number是否有值要小心： 

	//不要这样，会把负数都过滤掉 
	if(temp){} 
	//建议这样 
	if(!isNaN(temp)){}

· 善用getter和setter，以保护数据安全（必要的时候还要return data.clone()）和规范
· MonsterDebugger是个好东西
· Object和*作为数据类型是不严谨的，如果要复用，最好有具体的类型
· 初始化工作不在变量声明时进行，而是单独提取出来放入自定义函数init()进行，这样就可以重复初始化。
· 视图对象侦听Event.ADDED_TO_STAGE是个好习惯，在添加到舞台后就可以访问stage了。

· 命名规范化：

	//变量 下划线(私有时)+变量名(骆驼命名法)+类型说明(类名缩写/人为归类/不写)
	private var _mainMenuView:Sprite
	//常量 全大写+下划线
	public static const MAIN_MENU:String="mainMenu";
	//包名 驼峰法(仅app名称大写)
	me.rainssong.AppName.view
	//类名 帕斯卡命名法+说明(人为分类)
	MainMenuView
	事件名称避免重复，采用类名+事件名作为事件的type可避免重名

· 给位图绑定类（尤其是被大量使用的位图），否则会被做为Shape使用影响效率

· array.push.apply 比 array.concat快很多


雨声敲敲
2013-11-12