title: sort函数原理 
date: 2012-09-22 19:11 
tags: 
- AS3
- Array
categories:
- AS3
---


Array的sort函数可以对数组进行排序。他究竟是怎么工作的呢？

我们利用自定义比较函数对其进行测试，看看能不能发现什么。

使用 比较函数的原理 （摘自Adobe说明）： 
此方法使用语法和参数顺序 Array.sort(compareFunction, sortOptions)，其参数定义如下：
compareFunction - 一个用来确定数组元素排序顺序的比较函数。此参数是可选的。比较函数应该用两个参数进行比较。给定元素 A 和 B，compareFunction 的结果可以具有负值、0 或正值：
若返回值为负，则表示 A 在排序后的序列中出现在 B 之前。
若返回值为 0，则表示 A 和 B 具有相同的排序顺序。
若返回值为正，则表示 A 在排序后的序列中出现在 B 之后。 


请注意，这里有一个 错误 ，正确说法应该是
若返回值<=-1，则表示 A 在排序后的序列中出现在 B 之前。 
若返回值>-1 && <1，则表示 A 和 B 具有相同的排序顺序。 
若返回值>=1，则表示 A 在排序后的序列中出现在 B 之后。 

原因我猜想可能是 compareFunction 的返回值会被取整吧。

实验： 
新建一个函数来做测试。让每次都返回1，于是A就肯定会去B后面

    private function sortTrace(arr:Array):Array
    {
      var outputArr:Array = arr.slice();
      outputArr.sort
      (
        function(a:*,b:*):Number
        {
          trace(a, b);
          return 1;
        }
      );
      trace("currentArr",outputArr);
      return outputArr;
    }

然后sortTrace([1,2,3,4,5]) 

输出的是：//后为猜想的数组结果
2 3 //13245
5 3 
4 3 
1 3 //31245
2 3 //这里重复比较了，估计adobe的工程师加班了？
1 4 //34215
5 4 
2 4 
1 4 
1 2 
1 5 //34251
2 5 //34521

currentArr 3,4,5,2,1

结论： 
根据输出猜测是快速排序法

注意： 
不要用sort来进行随机排序，因为快速排序法是一种不稳定的排序法！因此无法保证每个数获得相同的待遇，会导致每种结果出现的概率不尽相同。 