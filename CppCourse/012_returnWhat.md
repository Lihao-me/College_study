# 返回什么才好呢
***
#### 2020.0404

### 描述
>程序填空，使其按要求输出
```c++
#include <iostream>
using namespace std;
class A {
public:
    int val;

    A(int
// 在此处补充你的代码
};
int main()
{
    int m,n;
    A a;
    cout << a.val << endl;
    while(cin >> m >> n) {
        a.GetObj() = m;
        cout << a.val << endl;
        a.GetObj() = A(n);
        cout << a.val<< endl;
    }
    return 0;
}
```

### 输入 
>多组数据，每组一行，是整数 m 和 n

### 输出 
>先输出一行： 123 然后，对每组数据，输出两行，第一行是m,第二行是n

### 输入样例
>2 3        
4 5         

### 输出样例
>123        
2        
3         
4        
5            

### 代码
```c++
#include <iostream>
using namespace std;
class A {
public:
    int val;

    A(int
 n = 123)
    {
        val = n;
    }
    A& GetObj()
    {
        return *this;
    }// 在此处补充你的代码
};
int main()
{
    int m,n;
    A a;
    cout << a.val << endl;
    while(cin >> m >> n) {
        a.GetObj() = m;
        cout << a.val << endl;
        a.GetObj() = A(n);
        cout << a.val<< endl;
    }
    return 0;
}
