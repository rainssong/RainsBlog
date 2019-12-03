title: Adobe系列软件更换语言和找不到扩展的问题
date: 2013-10-29 17:05 
tags: 
- Adobe
categories:
- IT
---

Adobe软件即使是非多语言版也会自动检测语言包。利用这一特性我们可以轻松修改Adobe软件的语言 

打个比方，Flash CS 6繁体版安装目录下有zh_TW文件夹。只要删除它Flash就会变成英文版，如果更换成一个简体中文包zh_CN就会变成简体中文版。

问题是，在你替换之后， Flash CS知道自己是中文版了，但是Adobe Extension Manager不知道，它依旧会把扩展安装到台湾版的目录下导致扩展失效，比如Win7 
C:\Users\[用户名]\AppData\Local\Adobe\Flash CS6\zh_TW。

解决方案：
1.C:\Users\ [ 用户名] \AppData\Local\Adobe\Flash CS6\zh_TW\Configuration下相应的扩展文件夹复制到 C:\Users\[ 用户名] \AppData\Local\Adobe\Flash CS6\zh_CN\Configuration下。 
2.再将 C:\Users\ [ 用户名] \AppData\Local\Adobe\Flash CS6\zh_TW\Configuration中WindowSWF文件夹复制到 C:\Users\[ 用户名] \AppData\Local\Adobe\Flash CS6\zh_CN\Configuration下 