# 填空题1
***
#### 2020.04.04

### 描述
>下面程序的输出是：
10
请补足Sample类的成员函数。不能增加成员变量。
```c++
#include <iostream>
using namespace std;
class Sample{
public:
    int v;
    Sample(int n):v(n) { }
// 在此处补充你的代码
};
int main() {
    Sample a(5);
    Sample b = a;
    cout << b.v;
    return 0;
}
```

### 输入 
>无

### 输出 
>10

### 输入样例 
>None

### 输出样例
>10

### 代码
```c++
#include <iostream>
using namespace std;
class Sample{
public:
    int v;
    Sample(int n):v(n) { }
    Sample(Sample& a)
    {
        v = 2 * a.v;
    }// 在此处补充你的代码
};
int main() {
    Sample a(5);
    Sample b = a;
    cout << b.v;
    return 0;
}
