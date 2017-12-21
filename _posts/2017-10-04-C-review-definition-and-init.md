---
layout: post           
title: C语言复习笔记一   
subtitle: 中秋节快乐！关于声明和初始化的一些易错点记录
image: /img/xuexi.jpeg
bigimg: /img/path.jpg
tags: [c,c++]  
---
### 声明和初始化过程：   
#### 1、连续声明：  

```  
char *p1,p2；等同于 char *p1；char p2；  
```  
#### 2、使用指针分配内存：  
```
	char *p = malloc（100）；或者  
	char *p ；p = malloc（100）；  
```
#### 3、声明（declaration）和定义（definition）全局变量的区别：  
``` 
	extern C语言中全局的声明标识符    
	声明：
	extern int i；
        extren  int f()；函数声明其实可以不需要extern
	对于函数，有没有extern声明都是一样的  
	定义：  
	int i = 0；这就是定义
	函数体定义就相当于提供了函数的声明；  
 ```
#### 4、static  和 extern ：  
```
在C中：
     1）static可以用来修饰局部变量、全局变量以及函数
        ·1 局部变量使用static修饰以后，作用于不改变，但是其存放到了静态数据区  
        （或者称它为全局数据区static），生命周期一直保留到程序执行结束，但是作用域仍然是在局部语句块。  
        static对本文件中全局变量进行声明，使该变量的作用域是只在此源文件中，对于函数等同于变量
        ·2 extern声明全局变量，其他的源文件也可以使用，改变了作用域为全局。
        在C++中：  
        static修饰函数以后，此函数变成此类的静态函数，不属于任何一个特定对象的函数。  
        如果其中某个变量使用static修饰以后，表示该变量为所有对象所有，保存唯一一个副本。  
        静态成员函数只能访问静态方法和变量，不能访问其他非静态成员或者变量。
	2）extern “此变量或者函数在别处定义，要在此处使用”。  
    	在file1.c中定义一个全局变量或者变量，可以在file2.c中调用。  
        使用extern比include速度快，可以加快编译过程。  
        在c+中extern有另外一种作用，指示使用c或者c++的调用规范，extern“c“ 告诉链接器使用c库函数和规范。  
```
### 类型typedef定义：  
#### 5、typedef 和 #define 的区别：  
```   
    在于能否正确处理指针定义：
	typedef  char *  String_t;
	#define  string_d  char*
	String_t  s1,s2;  //可以成功定义s1，s2
	string_d  s3，s4；//！！！s4只是char类型
    typedef还遵守作用域的优点  
```
#### 6、C中struct定义的方式：
```  
	struct  x1{...}；//使用方式： struct x1  a;
	typedef struct {...} x2；// 使用方式：x2 b;  
```
#### 7、const使用：
```  
如下定义：typedef char * charp；
         const charp p；
        p不可以改变，而不是p指向的字符
       typedef不会深入理解类型内部具体类型，  
       效果等同于const int i；i是不可以改变的
```