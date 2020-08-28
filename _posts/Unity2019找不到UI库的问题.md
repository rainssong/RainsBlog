
# Unity2019找不到UI库的问题

问题：突然找不到UI库
排查：UI库在PackageManager中，查看Git记录，VSCode插件更新过。更新VSCode插件，无效。重启VSCode，解决。
原因：VSCode更新后下载了C#编译器，编译器自作主张把dll删除了，但是又不能重新生成。

其它解决方案：
[Unity2019遇到UnityEngine.UI](https://www.taikr.com/app.php/article/3928)