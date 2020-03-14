# 重点防护
***
#### 2020.03.14

### 描述
>在战争中，物资运输和兵力运输是非常重要的，如果有一些位于重要交通线路上的城市万一落入到敌人手中，那么由于这城市的失陷，
使已方控制的区域就会被分割开来 （假设如果某座城市陷落，会导致其他城市变成孤城，那么这座城市就是重点城市），就会给自己
这一方造成战争中的被动。往往这些城市都是已方重点防护或敌人重点进攻的对象。假设你就是某军的最搞指挥官，当你无论拿到已方
地图或敌方地图，你能否尽快的在瞬息万变的战场形式下快速的找到要重点保护或是重点进攻的城市？       
输入      
输入有多组数据，每一组数据表示一张地图城市信息。每一组数据的第一行为一个整数Ｎ(Ｎ<=100),接着下面有m(m<=N)行描述这个地
图的数据。其中每一行由多个数据组成a1,a2,…..ak组成。表示城市a1和a2,….ak有道理相连，各个数据之间用空格分开，如：输入数
据5 1 2 3 4，那么表示，城市５和其它城市1,2 ,3, 4均有通路。每一组数据输入以0结束，整个输入同样以0结束。    
输出     
输出重点防护的城市个数。  
    
### 示例  
>输入样例 1          
5         
5 1 2 3 4       
0    
6    
2 1 3    
5 4 6 2    
0     
9     
2 1 3     
7 8     
5 6 4     
9 8    
0    
3    
1 2 3     
2 3     
0     
0     

>输出样例 1    
1    
2     
3    
0  

### 提示  
>可以将城市之间是否能到达通过二维数组的方式画成一个无方向路径图再进行分析，比如5 1 2 3 4可以画成：   
1 2 3 4 5     
1 - 0 0 0 1     
2 0 - 0 0 1     
3 0 0 - 0 1      
4 0 0 0 - 1     
5 1 1 1 1 -      
其中0表示不可到达，1表示可以到达。讨论自己能否到达自己在这一题没有意义。    
现在如果将5攻陷，那么第5行、第5列的所有1将会变成0。      
此时再检查其他城市，如果发现有的城市变成了孤城（横向纵向均为0），则说明被攻陷的城市是重点城市。     
城市5被攻陷后的路径图     
1 2 3 4 5     
1 - 0 0 0 0     
2 0 - 0 0 0     
3 0 0 - 0 0     
4 0 0 0 - 0     
5 0 0 0 0 -    
此时除了5外，1，2，3，4均变成了孤城。     

### 代码
```c++
#include <iostream>

using namespace std;
int* Links(int** city, int numsSize)
{
	static int* a = new int[numsSize + 1];
	for (int i = 0; i < numsSize + 1; i++)        
		a[i] = 0;    
	int temp;    
	for (int i = 1; i < numsSize + 1; i++) 
	{ int counts = 0;        
	for (int j = 1; j < numsSize + 1; j++) 
	{ 
		if (city[i][j] == 1) 
	{ 
			counts++;                  
	        temp = j;
	}
	}       
	if (counts > 1)           
		continue;        
	else { a[temp] = 1;
	} 
	}    
	return a;
}
int CountDangerCitys(int* link, int numsSize)
{
	int counts = 0;

	for (int i = 1; i < numsSize + 1; i++)

		if (link[i] == 1)

			counts++;

	return counts;

}
int CountCitys(int numsSize) {    
	int **City = new int *[numsSize + 1];    
	for (int i = 0; i < numsSize + 1; i++)       
		City[i] = new int[numsSize + 1];    
	for (int i = 0; i < numsSize + 1; i++)        
		for (int j = 0; j < numsSize + 1; j++)            
			City[i][j] = 0;
	int head_num;    
	bool Ishead = true;    
	while (true){           
		char temp;            
		temp = cin.get();           
		if (temp == '\n'){                
			Ishead = true;                
			continue;            
		}            
		if (temp > 48 && temp <= 57)            
		{                
			if (!Ishead)                
			{                    
				City[head_num][temp - 48] = 1;                    
				City[temp - 48][head_num] = 1;                    
				continue;                }                
			else if (Ishead)                
			{                   
				head_num = temp - 48;                    
				Ishead = false;               
			}            
		}           
		if (temp == '0')                
			break;        
	}    
	int *link = Links(City, numsSize);        
	int result = CountDangerCitys(link, numsSize);    
	return result;
}
int main() {
	int n = 1;    
	       
	while (n != 0)    
	{        
		cin >> n;
	       
	getchar();        
	if (n == 0)            
		break;        
	int result;        
	result = CountCitys(n);       
	cout << result << "\n";            
	}         
	return 0;
}
```

https://blog.csdn.net/Zxl19990529/article/details/79521981
