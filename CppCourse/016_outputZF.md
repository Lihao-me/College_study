# 填空题1
***
#### 2020.04.04

### 描述
下面程序输出的结果是：
0
5
请填空：
```c++
#include <iostream>
using namespace std;
class A {
public:
    int val;
// 在此处补充你的代码
};
main()  {
    A a;
    cout << a.val << endl;
    a.GetObj() = 5;
    cout << a.val << endl;
}
```

### 输入 
无

### 输出 
>0           
5          

### 输入样例 
None

### 输出样例
>0          
5             

### 提示
所缺代码具有如下形式：
```
    A(_________________ ){ val = n; }
    ________________ GetObj() {
        return _________________;
    }
```

### 代码
```c++
#include <iostream>
using namespace std;
class A {
public:
    int val;
A(n*3),val(n*2)// 在此处补充你的代码
};
main()  {
    A a;
    cout << a.val << endl;
    a.GetObj() = 5;
    cout << a.val << endl;
}
