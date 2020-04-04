# 简单的学生信息处理程序实现
***
#### 2020.04.04

### 描述
>在一个学生信息处理程序中，要求实现一个代表学生的类，并且所有成员变量都应该是私有的。
（注：评测系统无法自动判断变量是否私有。我们会在结束之后统一对作业进行检查，请同学们严格按照题目要求完成，否则可能会影响作业成绩。）

### 输入 
>姓名，年龄，学号，第一学年平均成绩，第二学年平均成绩，第三学年平均成绩，第四学年平均成绩。
其中姓名、学号为字符串，不含空格和逗号；年龄为正整数；成绩为非负整数。
各部分内容之间均用单个英文逗号","隔开，无多余空格。

### 输出 
>一行，按顺序输出：姓名，年龄，学号，四年平均成绩（向下取整）。
各部分内容之间均用单个英文逗号","隔开，无多余空格。

### 样例
>输入：Tom,18,7817,80,80,90,70    
输出：Tom,18,7817,80       

### 代码
```c++
#include<iostream>
#include<string.h>
using namespace std;
class Student {
private:
	char name[20];
	char id[10];
	int age;
	int s1, s2, s3, s4;
public:
	char* Name(const char* Oname);
	int Age(const int Oage);
	char* ID(const char* Oid);
	int Mean(int Os1, int Os2, int Os3, int Os4);
};
char* Student::Name(const char* Oname){
	strcpy(name, Oname);//strcpy_s在poj上无法通过
	return name;
}
int Student::Age(const int Oage) {
	age = Oage;
	return age;
}
char* Student::ID(const char* Oid) {
	strcpy(id, Oid);
	return id;
}
int Student::Mean(int Os1, int Os2, int Os3, int Os4) {
	s1 = Os1;
	s2 = Os2;
	s3 = Os3;
	s4 = Os4;
	return (s1 + s2 + s3 + s4) / 4;
}
int main() {
	char name[20];
	char id[10];
	char dot;
	int age;
	int s1, s2, s3, s4;
	cin.getline(name, 20, ',');
	cin >> age >> dot;
	cin.getline(id, 10, ',');
	cin >> s1 >> dot >> s2 >> dot >> s3 >> dot>> s4;
	Student S;
	cout << S.Name(name) << ',' << S.Age(age) << ',' << S.ID(id) << ',' << S.Mean(s1, s2, s3, s4) << endl;
	return 0;
}
