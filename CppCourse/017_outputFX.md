# 填空题2
***
#### 2020.04.04

### 描述
>下面程序输出的结果是：
4,6
请填空：
```c++
#include <iostream>
using namespace std;
class A {
        int val;
    public:
        A(int n) { val = n; }
        int GetVal() { return val; }
};
class B: public A {
    private:
        int val;
    public:
        B(int n):
// 在此处补充你的代码
        { }
        int GetVal() { return val; }
};
int main() {
    B b1(2);
    cout << b1.GetVal() << "," << b1.A::GetVal() << endl;
    return 0;
}
```

### 输入 
>无

### 输出 
>4,6

### 输入样例 
>None

### 输出样例
>4,6

### 提示
>本题需要用到继承构造函数。
其中 B():A(){...}表示B以无参数的形式继承A的构造函数。
B(int n) :A(n) {...}表示B以有参数的形式继承A的构造函数，并直接将用于构造A的形参n用于B的构造
B(int n) :A(n),val(n){...}表示B以有参数的形式继承A的构造函数，并直接将用于构造A的形参n用于B的构造，同时将n的值赋给B的val。
注意：在继承结构中，A的val与B的val是不同的！

### 代码
```c++
#include <iostream>
using namespace std;
class A {
        int val;
    public:
        A(int n) { val = n; }
        int GetVal() { return val; }
};
class B: public A {
    private:
        int val;
    public:
        B(int n):
A(int n=0){val=n;}
A&GetObj(){
	return *this;
}// 在此处补充你的代码
        { }
        int GetVal() { return val; }
};
int main() {
    B b1(2);
    cout << b1.GetVal() << "," << b1.A::GetVal() << endl;
    return 0;
}
