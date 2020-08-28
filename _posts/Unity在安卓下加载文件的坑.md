# Unity在安卓下加载文件的坑

关键词：Application.PersistentData  UnityWebRequest Android 

Unity加载本地文件的话，通常直接File.Load即可

但是安卓有特殊要求：

1. 如果加载Application.StreamingAssets需要用UnityWebRequest（除非AssetBundle），这个地址默认包含jar:file://前缀。
2. 如果加载Application.PersistentData，也可以用UnityWebRequest来加载，但问题又来了，地址前必须加上file://，这是很多教程没有写到的。File的话也许不用。