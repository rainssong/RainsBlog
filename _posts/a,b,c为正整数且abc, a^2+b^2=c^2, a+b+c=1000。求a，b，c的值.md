title: "a,b,c为正整数且a<b<c, a^2+b^2=c^2, a+b+c=1000。求a，b，c的值"
date: 2015-04-21 02:08 
tags: 
- AS3
- GameDevelop
- Math
categories:
- GameDevelop
---

由题目可分析得：C<500，因此第一层从500开始递归，这样有个好处，【500到C的距离】肯定小于【0到A的距离】。
如果思路比较清楚的话会写成这样：

		private function calc():void
		{
		        for (var k:int = 499; k > 0; k--)
		                for (var j:int = k - 1; j > (1000-k-j); j--)
		                {
		                        var i:int = 1000 - i - j;
		                        if (i * i + j * j == k * k)
		                        {
		                                trace(i, j, k);
		                                return;
		                        }
		                }
		}
		有童鞋直接把三元方程组降元后写出了更高效率的公式：
		private function calc():void
		{ 
		    for(a = 333; a > 0; a --)
		     {
		             b = (500000- 1000* a) / (1000- a);
		             c = 1000- a - b;
		             if(a * a + b * b == c * c)
		             {
		                     trace(a,b,c);
		                     return;
		             }
		     }
		}

像这种算法题，核心思想就是：人可以受累，让计算机尽量少算。