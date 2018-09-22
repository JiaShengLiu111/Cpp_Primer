

# 一、输入数据

## 1.1 输入诺干整数。

> 要求：不指定输入的整数个数，输入以换行符结束，数字之间使用空格分隔。

```
vector<int> readline()
{
	vector<int> result;
	for (int i = 0;; i++)
	{
		int tmp = 0;
		cin >> tmp;
		result.push_back(tmp);
		if (getchar() == '\n')
		{
			break;
		}
	} 
	return result;
}

```

## 1.2 输入若干字符串

> 要求：不指定输入的字符串个数，输入以换行符结束，字符串之间使用空格分隔。

```
vector<string> readline()
{
	vector<string> result;
	for(int i=0;;i++)
	{
        string str;
		cin>>str;
		result.push_back(str);
		if(getchar()=='\n')
		{
			break;
		}
	} 
	return result;
}

```

**总结**：上面两个函数都是通过getchar()函数从而实现“回车”停止输入的功能。

# 二、大整数问题

# 三、stringstream类

C++中stringstream类和java中StringBuffer类似，可以做字符串拼接的功能。需要的头文件为sstream

> 拼接字符串：

```
stringstream ss;
ss<<str;   // 字符串拼接
ss.str()  // stringstream转string
```



# 四、关于#include<*.cpp>用法问题

> 定义解释:

所谓include的意思，其实就是将被包含的文件内容复制到#include处，无论被包含的文件是.h后缀，或者是.cpp后缀。

> something wrong：

假如你在一个cpp文件中include同一个工程中的另外一个cpp文件，对于新手而言，在程序链接时常常会出现重定义的错误。之所以会出现这种错误，是因为同一个工程中两个不同的cpp文件中可能包含了相同的定义，这对于c++而言是不允许的【为什么不允许这么做，见解释一】。c++中常见的定义主要包含：变量的定义，函数的定义，结构体的定义（注意：通过typedef定义的结构体是允许重复的，详见解释二）等。

**总结+注意**：c++中仅仅要求cpp文件不能包含重复的定义。h头文件是没有这个要求的，即假如某个h头文件中包含了重复定义，只要它没有被include到cpp文件中都是没有问题的，根本原因在于编译器不会编译h头文件。



> 解释一：为什么c++中不允许两个不同的cpp文件中包含相同的定义？

不管两个cpp文件最终会不会被include到一块，只要它们包含了相同的定义，在进行程序编译时都是会报错的。根本原因不在于它们是不是最终会被include到同一个文件，而是在于编译器会编译所有的cpp文件。假如两个cpp文件包含两个同名的函数，编译器就疑惑了，当主程序中调用该函数时，编译器不知道具体应该调用哪个函数，所以这也是编译器对于该问题报错的根本原因。

> 解释二：为什么两个不同的cpp文件中允许两个相同的通过typedef定义的结构体？

```
typedef struct Node
{
    int data;
    struct Node* next;
}LinkList;
```

之所以允许这种操作，其实就相当于你在同一个文件中写两遍，如下所示：

```
typedef int ElemTpye；
typedef int ElemTpye；
```

在进行程序编译时，编译器是不会报错的，准确来说，这种操作不应该算是变量定义的范畴，而是类型定义。



# 五、关于结构体

> 结构体的定义

```
struct student
{ 
	string name;
	int age;
};
```

如上所示，定义一个结构体，就相当于定义了一种新的类型，该类型的名称为struct student，或者是student。

> 使用typedef定义结构体

```
typedef struct student
{ 
	string name;
	int age;
}Stu;
```

相当于通过typedef，给定义的结构体类型取一个新的名字Stu，此时Stu和struct student或者student是等价的。

> 结构体重定义问题

```
struct student
{
	string name1;
	int age;
}; 
struct student
{
	string name2;
	int age;
}; 
```

结构体重定义问题的关键不在于结构体内部如何，而在于结构体名。如上代码块，定义了两个同名的结构体，编译器不知道应该使用哪一种定义，所以会出现编译错误。
