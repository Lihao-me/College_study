# 做游戏
***
#### 2020.03.07

### 问题
>描述:
有M个小孩子围成一圈做游戏，每个小孩子都有一个初始的号码。游戏有X步，每一步的操作方法都相同：每个小孩子把自己手上
的号码改写成自己（原来的号码加上右手边的小孩子的号码）除以100的余数。请问你：经过X步之后，每个小孩子手上的号码是
多少？ 比如：有3个初始编号为{1，2，3}的小孩子，第一步操作完成之后，他们的编号变成了{1+2，2+3，3+1}即{3，5，4}。
输入:
输入有N组测试数据。每组测试数据有2行： 第一行包含M和X。 第二行包含M个不超过100的整数。
输出 :
输出数据有N行，每行是一组测试数据的结果。注意：两个数字之间只有一个空格。每行以一个空格结尾。
提示
若只有一个小孩子，有初始号码x，则一步结束后结果为x + x(也需考虑%100)。　

### 示例
>输入：                                
2                                  
3 1  
1 2 3  
3 2  
1 2 3  

>输出：                                                
3 5 4                                   
8 9 7  

### 思路
>除最后一个数外前一个数加后一个数，最后一个数加最开始的第一个数，重复所要求次数。同时也要考虑一个人时候的特殊情况。

### 代码
```c++
#include<iostream>
using namespace std;
int main() {
	int n;
	cin >> n;
	while (n != 0) {
		n = n - 1;
		int m, x;
		cin >> m >> x;
		int* chil = new int[m];
		for (int i = 0; i < m; i++) {
			cin >> chil[i];
		}
		while (x != 0) {
			x = x - 1;
			if (m == 1) {
				chil[0] = (chil[0] + chil[0]) % 100;
			}
			else {
				int wai = chil[0];
				for (int i = 0; i<m-1; i++) {
					chil[i] = (chil[i] + chil[i + 1])%100;
				}
				chil[m - 1] =( chil[m - 1] + wai)%100;
			}
		}
		for (int i = 0; i < m; i++) {
			cout << chil[i] << " " ;
		}
		cout << endl;
		
	}
	return 0;
}
```

### 分析
 - 这道题需要注意的是多组数据的输入和循环。

上一题：[6174猜想](https://github.com/Lihao-me/College_study/blob/master/CppCourse/002_6174thinking.md)                
下一题：[比较版本](https://github.com/Lihao-me/College_study/blob/master/CppCourse/004_versionCampare.md)       
