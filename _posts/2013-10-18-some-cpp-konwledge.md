---
layout: post
category : cpp related
title : "最近查过的一些C++知识"
tagline: "每天学一点"
tags : [camera, third person view]
---
{% include JB/setup %}

又好久没发博了，最近发现很多C++的知识还是挺琐碎的，需要整理，一点点来吧。
####typedef用法

	typedef int Size; // Size size;
	typedef char Line[100]; // Line line;
	typedef char * pstr; // pstr ps1, ps2; 相对于#define的优势，用#define要写pstr ps1, * ps2;
	typedef const char * cpstr; // cpstr cps; const cpstr ccps; 前者是指向常量的指针，后者是指向常量的常指针；
	typedef int (*PF)(const char *, const char *);
	例： 
	typedef void (*pFunParam)();
	typedef void (*pFun)(pFunParam);
	pFun b[10]; // void (*b[10])(void(*)());
	
####存储类关键字

typedef: 只占用声明中的存储类关键字位置，不起存储作用。  

auto: 默认的变量存储类型，说明变量具有自动存储时期。  

static: 静态存储，程序运行期间不释放，只初始化一次。
      PS: 静态全局变量——只在当前文件内可访问，其他文件内即使extern也无法访问。  
	  
register: 用寄存器存取提高效率，声明仅仅作为请求，具体行为由编译器决定。
      1. 只有局部自动变量和形式参数可以作为寄存器变量
	  2. 不能定义任意多个寄存器变量  
	  
extern: 外部全局变量。  

volatile: 用volatile声明的变量程序总是从它所在内存读取数据，而不使用任何效率优化措施。防止编译器对该变量的存取作出效率优化，防止其他线程，系统或硬件原因导致的意外修改变量值。volatile变量可为const。  

restrict: 只用于限定指针，该关键字用于告知编译器，所有修改该指针指向内容的操作全部都是基于该指针。
      1. 告诉编译器可以放心进行优化
	  2. 告诉用户要使用符合restrict要求的参数  
	  
mutable: 使类中的const方法可以修改被该关键字声明的成员。  

	