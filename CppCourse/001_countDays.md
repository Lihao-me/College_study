# 日期计算
*** 
#### 2020.03.02

### 问题
>描述
输入3行数据，分别是：某年1月1日是星期几（一位数字，其中星期日用0表示），这一年是否为闰年（用p和r分别表示平年和闰年），
某个日期（月和日之间用空格隔开）。输出这一天是星期几（用英语大写前3个字母表示）。
输入 
3行数据，分别是：
某年1月1日是星期几（一位数字，其中星期日用0表示）
这一年是否为闰年（用p和r分别表示平年和闰年）
某个日期（月和日之间用空格隔开）
输出 
这一天星期几（用英语大写前三个字母表示）。

### 示例
输入：      
```
0

p

3 1
```

输出：
```
WED          
```

### 思路
>首先算出从所给年月日到一月一号有几天，从而根据除以七3的余数得到改天星期几。

### 代码
```c++
#include<iostream>
using namespace std;
int main() {
	int first, month, day;
	char judge;
	cin >> first;
	cin >> judge;
	cin >> month >> day;
	int month_array[12] = { 31,28,31,30,31,30,31,31,30,31,30,31 };
	if (judge == 'r')
		month_array[1] = 29;
	for (int i = 0; i < month - 1; i++) {
		day = day + month_array[i];
	}
	int res;
	res = day % 7;
	if (res + first >= 7)
		res = res + first - 8;
	else
		res = res + first-1;
	switch (res) {
	case 0: cout << "SUN" << endl; break;
	case 1:cout << "MON" << endl; break;
	case 2:cout << "TUE" << endl; break;
	case 3:cout << "WED" << endl; break;
	case 4:cout << "THU" << endl; break;
	case 5:cout << "Fri" << endl; break;
	case 6:cout << "SAT" << endl; break;
	//default:cout << "error" << endl;
	}
	return 0;
}
```

### 分析
 - 时间: 2ms 内存: 3MB 语言: C++。
 - 其实开始的时候考虑的有点狭隘了，在纠结天数怎么简便的算出来，实际上只要一个数组就搞定啦。我也趁热打铁在LeetCode上找了一道日期类的题，详见LeetCode
    仓库：https://github.com/Lihao-me/LeetCode_Practice/blob/master/LeetCode_Easy/040_dayOfYear.md 。

下一题：[6174猜想](https://github.com/Lihao-me/College_study/blob/master/CppCourse/002_6174thinking.md)
