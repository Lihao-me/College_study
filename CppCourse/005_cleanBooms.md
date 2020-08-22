# 扫雷计数
***
#### 2020.03.04

### 描述
>扫雷（Minesweeper）是一个有趣的小游戏。玩家需要根据数字的提示，在不触雷的条件下把所有不是雷的区域翻开才能胜利；
一旦触雷即告失败。扫雷游戏的高级（16x30，99雷）世界纪录为31.133秒，由波兰人KamilMuranski保持。扫雷盘面中，某格
中数字的含义是其周围相邻8格（如果是边界或角则相应为5格或3格）中含有的雷的个数。相信大家通过对于上图的分析，能够理解这个含义。 
本题要求对于一个雷区（给定大小以及雷的位置），计算盘面所有数字的和。
雷区大小8行8列，共含有10个雷，盘面上有18个1，6个2以及4个3，故数字总和为18+ 2x6 + 3x4 = 42。 

### 示例
>输入 :
输入包含若干行。
第一行是两个整数M，N，以空格分开，代表雷区的行数和列数。1 <= M <= 50，1 <= N <= 50。
第二行是一个整数K，代表雷区中雷的个数，0 <= K <= M*N。
接下来K行代表K个雷的位置，每行有两个用空格分开的整数，分别代表这个雷的所在的行R（1 <= R <=M）和列C（1 <= C <=N）。数据保证这K行中没有重复。 
输出: 
一个整数，代表该雷区中所有数字之和。注意，如果一个雷区中全是雷，其数字之和为0；如果一个雷区中没有雷，其数字之和也为0。   
    
>输入样例1    
8 8
10
1 1
1 7
3 8
4 4
4 8
5 8
6 3
6 8
7 8
8 8   

>输出样例1     
42

### 代码
```c
#include<stdio.h>
int main() {
	int r, c, num;
	scanf("%d %d", &r, &c);
	scanf("%d", &num);
	if (c * r == num || num == 0) {//排除特殊情况
		printf("0\n");
		return 0;
	}
	if (c * r == 1) {
		printf("0\n");
		return 0;
	}
	int arr[52][52] = { 0 };
	int m, n;
	for (int k = 0; k < num; k++) {//将雷赋为-1
		scanf("%d %d", &m, &n);
		arr[m][n] =-1;//将雷区外一周贴边
	}
	for (int i = 1; i < r + 1; i++) {
		for (int j = 1; j < c + 1; j++) {
			if (arr[i][j] == -1) {
				for (int p = i - 1; p <= i + 1; p++) {
					for (int q = j - 1; q <= j + 1; q++) {
						if ((p != i || q != j)&&arr[p][q]!=-1)//将雷一周加1
							arr[p][q]++;
					}
				}
			}
		}
	}
	int sum = 0;
	for (int x = 1; x < r + 1; x++) {
		for (int y = 1; y < c + 1; y++) {
			sum = sum + arr[x][y];//计算雷区数字和
		}
	}
	sum = sum + num;//将雷的-1加上1抵消
	printf("%d\n", sum);
	return 0;
}
```

上一题：[比较版本](https://github.com/Lihao-me/College_study/blob/master/CppCourse/004_versionCampare.md)       
下一题：[有序链表插入](https://github.com/Lihao-me/College_study/blob/master/CppCourse/006_insertNode.md)  
