# 岛屿周长
***
#### 2020.03.14

### 描述
>用一个nm的二维数组表示地图，1表示陆地，0代表海水，每一格都表示一个11的区域。地图中的格子只能横向或者
纵向连接（不能对角连接），连接在一起的陆地称作岛屿，同时整个地图都被海水围绕。假设给出的地图中只会有
一个岛屿，并且岛屿中不会有湖（即不会有水被陆地包围的情况出现）。请判断所给定的二维地图中岛屿的周长。
输入 :    
第一行为n和m，表示地图的大小(1<=n<=100, 1<=m<=100)。接下来n行，每行有m个数，分别描述每一格的数值。数值之间均用空格隔开。
输出 :    
只有一行，即岛屿的周长（正整数）。

### 示例
输入样例 1     
3 4
1 1 1 0
0 1 0 0
1 1 0 0

输出样例 1   
14    

### 代码
```c
#include<stdio.h>
int main()
{
	int n, m;
	scanf("%d %d", & n, & m);
	int area[101][101];
	for (int i = 0; i < n; i++) {
		for (int j = 0; j < m; j++) {
			scanf("%d", &area[i][j]);
		}
	}
	int sum=0;
	for (int i = 0; i < n; i++) {
		for (int j = 0; j < m; j++) {
			if (area[i][j] == 1)
				sum++;
		}
	}
	for (int i = 0; i < n-1; i++) {
		for (int j = 0; j < m - 1; j++) {
			if (area[i][j] == 1 && area[i + 1][j] == 1 && area[i][j + 1] == 1 && area[i + 1][j + 1] == 1)
				sum--;
		}
	}
	sum = 2 * sum + 2;
	printf("%d\n", sum);
	return 0;

}
```

上一题：[倒过来输出](https://github.com/Lihao-me/College_study/blob/master/CppCourse/007_reverseOutput.md)     
下一题：[重点防护](https://github.com/Lihao-me/College_study/blob/master/CppCourse/009_mainProtect.md)
