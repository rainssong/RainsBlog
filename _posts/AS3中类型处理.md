title: "as3中类型处理：typeof,is,as,instanceof,getqualifiedclassname等 "
date: 2013-05-08 19:51  
tags: 
- AS3
categories:
- AS3
---

1.is——判断对象/类是否属于某一类，返回布尔值
例：123 is Number
返回:true
例：int is Object
返回：true

2.as——弱转换，不会丢失数据，仅在类型链有效（转换为父类对象）， 失败返回 null
例: 123 as uint
返回：123
例：123 as string
返回：null
注：在很多情况下，类型不符时编译器会自动进行弱转换


3.Class(object)——强转换，可能丢失数据，适用范围较广，失败抛出错误
例：int(123.45)
返回 123

4.typeof—— 以字符串形式返回对象的类型， 不推荐使用 
例：typeof "test" 
返回："string"

5.instanceof——和is相同，但不能判断接口， 不推荐使用 

6.getDefinitionByName——根据类名获取类

7.getQualifiedClassName——获取完整 类 名

8.getQualifiedSuperclassName——获取完整 父类 名

9.constructor根据对象获取类， 需要转换为Object对象否则编译不通过 
例：obj1.constructor
返回：[class Object]

雨声敲敲
2013-5-8