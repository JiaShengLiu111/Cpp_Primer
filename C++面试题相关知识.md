

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





































