title: "是时候总结一下Vector和Array了"
date: 2015-01-12 17:32
tags: 
- AS3
- Array
categories:
- AS3
---
作者：雨声敲敲
blog：blog.sina.com.cn/rainssong
homepage：rainsgameworld.sinaapp.com/
weibo：weibo.com/rainssong
转载请注明

	搜了一些相关帖子，发现有的讲解不全，有的误导观众，故而总结与此。以供新手学习。

	1.初始化和类型检查
	Array没有类型检查，但不代表Array不支持类型定义，Look：
	var arr:Array.<Number> = [1, 2, 3, 4, 5,"a"];
	//这样写的好处是——有代码提示！坏处是——依旧不规范，因为编译器不会提示你"a"元素的错误。还是要自己多加注意。

	Vector有类型检查，但是也可以没有！Look：
	var vec:Vector.<Number> = new <Number>[1,2,3,4,5,"a"];//报错！
	var vec:Vector.<*> = new <*>[1,2,3,4,5,"a"];//不报错但不建议

	2.效率
	没有绝对高下之分，总的来说，Array处理复杂类型时更快（如Object），Vector处理基础类型（如Number String）更快。具体资料可自行搜索。

	3.功能
	Array有sortOn方法，可以排序复杂对象。
	Vector可以固定长度，防止出错。

	4.转换
	Array转为Vector十分简单：
	var vec:Vector.<Number> = Vector.<Number>(arr);

	Vector转Array却很麻烦，需要自行遍历，但事实上你基本没有必要将Vector转换为Array，大部分时候只需要这么做就好了：
	var arr:Array.<Number> = vec;
