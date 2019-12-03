title: "判断AS3程序是否为debug版本"
date: 2012-09-28 14:22 
tags: 
- AS3
categories:
- AS3
---

有两种方法： 

1.利用try catch

    public function getisDebugMode():Boolean 
    { 
      try 
        trace(Object("").fuck);
      catch(e:Error) 
        return true;
      return false;
    }

2.利用编译参数(FlashDevelop会自动添加此参数)

    private function getisDebugMode():Boolean 
    {
      return CONFIG::debug ; 
    }

推荐第一种方法省事。还可以自己加一个记录变量减少判断次数。第二种方法如果你用了。不如干脆直接进行条件编译，也不需要判断了 。