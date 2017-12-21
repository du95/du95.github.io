---
title: strlen()和sizeof()
description: 众所周知，凡是学习C/C++语言的过程中，遇到字符串的问题或者是数组的问题，我们八成会用到这两个函数，在使用中其实有很多陷阱，今天看到恍然大悟，并结合之前的案例进行说明。
categories:
 - C/C++
tags:
---
## strlen()和sizeof()的区别  
#### 1.strlen()  
> strlen()是函数，在运行时计算，即在程序执行以后计算数组的实际长度，注意时实际长度，并且要‘\0’结尾才可以。使用时参数传入以指针的形式，因为数组名在作为参数传入的时候就退化成了指针  
> 例如：定义一个字符数组  char str[20] = "hello world";  
> 使用方式就是：strlen(char*) 即strlen(str);
> *且长度等于实际长度11,而不是20

#### 2.sizeof()  
> sizeof()是运算符，所谓运算符和函数的差别就是，sizeof的使用在程序编译的时候就计算出来了，用于计算数据空间的字节数。因此，sizeof不能用于计算动态分配的空间的大小。sizeof常用于返回类型和静态分配对象、结构或者数组占用的空间，返回值的大小和结构所存储的内容没有关系。  
> 这让我想起了之前的一个例子：  

```
#include <iostream>
using namespace std;
int length(int* arr){
    cout<<"length函数中："<<endl;
    cout <<"sizeof(arr):"<<sizeof(arr)<<endl;
    cout <<"sizeof(int):"<<sizeof(int)<<endl;
    cout <<"length函数结束"<<endl;
    return (sizeof(arr)/sizeof(int));
}
int main(){
    int arr[10] = {9,8,0,6,1};
    cout << "length(arr)返回值:"<<length(arr) <<endl;
    cout <<"main 函数中sizeof(arr)/sizeof(int)：";
    cout << sizeof(arr)/sizeof(int)<<endl;
    return 0;
}
```  
结果：  
``` 
length函数中：
sizeof(arr):8
sizeof(int):4
length函数结束
length(arr)返回值:2
main 函数中sizeof(arr)/sizeof(int)：10
```  
> 这里结果和明显的告诉了我们函数在使用数组名传入参数时，退化成了指针。在子函数里面用sizeof计算传入数组的大小是不可行的，必须在main函数中将length计算出，作为参数一起传入子函数才行。在实际使用过程中，我们应该注意这一点，新手容易犯这类错误。  

---
> 另外：提供一个引用的使用案例，可以运行一下查看使用引用和不使用引用的差别，结果是使用了引用结果正确，不使用引用传入参数的子函数结果不正确  

``` 
/*
 * 这是一道算法题目：使用另一个栈与一个辅助元素空间，给另外一个栈排序
 */
#include <iostream>
#include <stack>
using namespace std;
//注意参数传入方式，这是正确版本引用传入
void sortStack(stack<int>& nStack){   
//传入方式注意，使用引用才可以真正传入栈地址，对其内容进行操作，
//否则无效！！！！可以将&删除，再运行结果就错了
    stack<int>tempStack;
    while(!nStack.empty()){
        int temp = nStack.top();
        nStack.pop();
        while(!tempStack.empty() && temp >tempStack.top() ){
            int temp1 = tempStack.top();
            nStack.push(temp1);
            tempStack.pop();
        }
        tempStack.push(temp);
    }
    while(!tempStack.empty()){
        int ntemp = tempStack.top();
        nStack.push(ntemp);
        tempStack.pop();
    }
}
void stackShow(stack<int>nstack){
    while(!nstack.empty()){
        cout<<nstack.top();
        nstack.pop();
    }
}
int main() {

    std::cout << "Hello, stack" << std::endl;
    stack<int>myStack;
    myStack.push(4);
    myStack.push(2);
    myStack.push(3);
    myStack.push(1);
    sortStack(myStack);
    stackShow(myStack);
    return 0;
}  
```   
---
> |读书笔记，学如逆水行舟，不进则退|  
> 如果有误，欢迎指正。908610627@qq.com

---
