# 奇怪的类复制
***
#### 2020.04.04

### 描述
程序填空，使其输出9 22 5
```c++
#include <iostream>
using namespace std;
class Sample {
public:
    int v;
// 在此处补充你的代码
};
void PrintAndDouble(Sample o)
{
    cout << o.v;
    cout << endl;
}
int main()
{
    Sample a(5);
    Sample b = a;
    PrintAndDouble(b);
    Sample c = 20;
    PrintAndDouble(c);
    Sample d;
    d = a;
    cout << d.v;
    return 0;
}
```

### 输入 
无
### 输出 
9
22
5

### 输入样例
>None
### 输出样例
>9           
22            
5           

### 代码
```c++
#include <iostream>
using namespace std;
class Sample {
public:
    int v;
    Sample(int n=0)
    {
        v=n;
    }
    Sample(const Sample &x)
    {
        v=x.v+2;
    }// 在此处补充你的代码
};
void PrintAndDouble(Sample o)
{
    cout << o.v;
    cout << endl;
}
int main()
{
    Sample a(5);
    Sample b = a;
    PrintAndDouble(b);
    Sample c = 20;
    PrintAndDouble(c);
    Sample d;
    d = a;
    cout << d.v;
    return 0;
}
