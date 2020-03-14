# 倒过来输出
***
#### 2020.03.14

### 描述
>输入 :一个整数n   
输出 :   
倒过来的整数

### 示例
>输入样例 1      
380    

>输出样例 1     
83   

### 代码
```c++
#include<iostream>
#include<limits.h>
using namespace std;
int main() {
	int result=0,x;
  cin>>x;
        int n=x;
        while(x!=0){
            if(result>INT_MAX/10) return 0;
            if(result<INT_MIN/10) return 0;
            result=result*10;
            result=result+x%10;
            x=x/10;
        }
  cout<<result<<endl;
          return 0;
}
