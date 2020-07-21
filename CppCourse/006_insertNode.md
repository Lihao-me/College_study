# 有序链表插入
***
#### 2020.03.07

### 描述
>描述
要求实现一个函数，在递增的整数序列链表（带头结点）中插入一个新整数，并保持该序列的有序性。  
其中单链表的结构定义如下： 
```c
typedef struct LNode   //定义单链表节点结构体

{  

     ElemType data;       //数据域

     struct LNode *next; //指向后继节点

} LinkList;
```
函数接口定义：
```c
void ListInsert(LinkList *&L, ElemType e);
```
输入：输入 
三行
行1 结点个数
行2 具体的节点数据值
行3 插入结点数据值 
输出 
有序链表数值

### 示例
>输入：    
5    
1 2 4 5 6   
3     

>输出：    
1 2 3 4 5 6   

### 代码
```c
#include<stdio.h>
#include<malloc.h>
struct num
{
    int n;
    struct num* next;
};
int main(void)
{
    struct num* head;
    struct num* Node;
    struct num* unit;  
    int n;
    scanf("%d", &n);
   Node = (struct num*)malloc(sizeof(struct num));
    head = Node;
    for (int i = 0; i < n; i++)
    {
        int j;
        scanf("%d", &j);
        Node->n = j;
       Node->next = new num;
      Node = Node->next;
    }
    Node->next = NULL;
    Node->n = 99999;
   Node = head;
    unit = (struct num*)malloc(sizeof(struct num));
    int j;
    scanf("%d", &j);
    unit->n = j;
    if (unit->n < Node->n) 
    {
        head = unit;
        unit->next = Node;
    }
    else  
    {

        while (unit->n > Node->next->n)
        {
            Node = Node->next;
        }
        unit->next = Node->next;
        Node->next = unit;
    }
    Node = head;
    while (Node->n != 99999)
    {
        printf("%d ", Node->n);
        Node = Node->next;
    }
}
```
