title: "提取swf中的ByteArray "
date: 2014-10-29 10:00 
tags: 
- AS3
categories:
- AS3
---

作者：雨声敲敲
blog： blog.sina.com.cn/rainssong 
homepage： rainsgameworld.sinaapp.com/ 
weibo： weibo.com/rainssong 


市面上的Flash反编译软件，能提取代码、动画、位图声音，却不能提取swf中的ByteArray以及ByteArrayAsset（资源被Embed以后即成为 ByteArrayAsset ）。于是只好自己动手。经过反复试验，现归纳步骤如下。 


1.加载swf：

		_loader.load(new URLRequest("GyakuSai5.swf"));

2.根据类名获取数据（类名在反编译时已经找到了）：

		var myClass:Class = _loader.contentLoaderInfo.applicationDomain.getDefinition("[类名]") as Class;
		var byteArray: ByteArrayAsset = new myClass asByteArrayAsset ;

第一句看不懂的自行搜索

3.导出文件，用FileStream类将byteArray导出为文件。如果byteArray是加密过的，还得解密。

用此法提取了《逆转裁判5 在线试玩版》的脚本，见：http://blog.sina.com.cn/s/blog_59fc39980102vbl5.html