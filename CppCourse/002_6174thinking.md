# 6174猜想
***
#### 2020.03.07

### 问题
>描述:
6174猜想 ，1955年，卡普耶卡(D.R.Kaprekar)研究了对四位数的一种变换：任给出四位数k0,用它的四个数字由大到小    
重新排列成一个四位数m,再减去它的反序数rev(m),得出数k1=m-rev(m),然后，继续对k1重复上述变换，得数k2.如此进                  
行下去，卡普耶卡发现，无论k0是多大的四位数， 只要四个数字不全相同，最多进行7次上述变换，就会出现四位数6174                   
输入:                              
输入一个四位数（四个数字不完全相同）                                                             
输出:                      
将这个四位数的四个数字重新排列组成一个最大的数和一个最小的数相减，得到一个新的四位数；重复操作，直到最终结果                   
为6174。每行输出一个算式，最后一行输出变换次数。         

### 示例
>输入：7888            
输出：                   
8887-7888=999，              
9990-999=8991，               
9981-1899=8082，             
8820-288=8532，             
8532-2358=6174；             
5                                      

### 思路
>先对各个数字进行由大到小排序再减去逆转的数，重复此操作直到得到6174.                           

### 代码
```c++
#include<iostream>
#include<algorithm>
using namespace std;
int reverse(int x)
{
    int n=x, result = 0;
    for(int i=0;i<4;i++){
        result = result * 10;
        result = result + x % 10;
        x = x / 10;
    }
    cout << n<< "-" << result<<"=" << n-result << endl;
    return n-result;
}
int main()
{
	int a, i=0;
	cin >> a;
    
	while (a != 6174) {
        int m[4];
        for (int i = 0; i < 4; i++) {
            m[i] = a % 10;
            a = a / 10;
        }
        a = 0;
        sort(m, m + 4, greater<int>());
        for (int i = 0; i < 4; i++) {
            a = a * 10 + m[i];

        }
        a = reverse(a);
        i = i + 1;
    }
    cout << i << endl;
    return 0;
}
```
### 分析
 - 这道题开始的时候错误频出，在于遗漏了很多条件，比如排序，每一次循环都要重新排序一次。这道题的简单之处在于只是四位数不用考虑溢出问题。而用algorithm
   下的sort进行排序则使用了其由大到小的排序方式非常方便。对于使用详情可见：https://blog.csdn.net/lytwy123/article/details/84503492 。
   
上一题：[日期计算](https://github.com/Lihao-me/College_study/blob/master/CppCourse/001_countDays.md)
下一题：[做游戏](https://github.com/Lihao-me/College_study/blob/master/CppCourse/003_playGames.md)
