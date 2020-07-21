# 比较版本
***
#### 2020.03.07

### 问题
>描述:
版本号是版本的标识号。可以假设版号只含数字和字符'.'，字符'.'代表的不是小数点，只是用来分隔每个数字。
比如，2.5表示的是"the fifth second-level revision of the second first-level revision"，而不是
"two and a half" 或者 "half way to version three"。例如，按版本先后顺序排序，有0.1 < 1.1 < 1.2 < 1.10 < 13.37。
现在的任务是，比较两个版本的版本号，输出较新的版本号。
输入:
输入为两行。分别为两个版本号，不含空格。
输出:
较新版本的版本号。

### 示例
>1.0.2  
1.1.2  

>1.1.2

### 思路
>
对从左到右的数依次比较，先出现较高数的则为最新版本。

### 代码
```c++
#include<iostream> 

using namespace std;
int main()
{
	int a1, b1, c1, a2, b2, c2;
	char x, y;
	cin >> a1 >> x >> b1 >> y >> c1;
	cin >> a2 >> x >> b2 >> y >> c2;
	if (a1 > a2||(a1==a2&&b1>b2)||(a1==a2&&b1==b2&&c1>c2))
		cout << a1 << x << b1 << y << c1 << endl;
	else
		cout << a2 << x << b2 << y << c2 << endl;
	return 0;
}
```

### 分析
 - 开始的时候一直在纠结该怎么读入这两行字符，其实不用考虑这么多简单的一个代码搞定。
 - 我也趁热打铁在LeetCode上找了一道类似的，也不是很复杂。详见：
 https://github.com/Lihao-me/LeetCode_Practice/blob/master/LeetCode_Medium/003_compareVersion.md
