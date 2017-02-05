#C++ Primer学习笔记-第一章-开始
------
##一些知识点
###IO库
- C++通过IO库（iostream）来提供IO机制
- 标准库有4个IO对象,cin,cout,cerr,clog
	- cerr：ostream对象，关联标准错误，通常写到和标准输出相同的设备，注意写到cerr的数据不缓冲，而写到cout的数据要先写入缓冲区，待写入换行或者buffer满时才输出到输出设备
	- clog：关联到标准错误，会先写入缓冲区
- 输入运算符>>,输出运算符<<接受一个左侧的IO对象，运行完结后会返回对应的对象，所以在代码里面可以看到<<,>>的连续使用
###文件结束符
- win中是ctrl+z，linux、mac中一般是ctrl+d
------
##练习题
###练习1.3
```cpp
#include<iostream>
using namespace std;

int main(){
	cout<<"hello world!"<<endl;
	return 0;
}
```
###练习1.4
```cpp
#include<iostream>
using namespace std;

int main(){
	int num1;
	int num2;
	cout<<"请输入两个整数："<<endl;
	cin>>num1>>num2;
	cout<<num1<<"和"<<num2<<"的和为"<<num1+num2<<",乘积为"<<num1*num2<<endl;
	return 0;
}
```
###练习1.9
```cpp
#include<iostream>
using namespace std;

int main(){
	int sum = 0;
	int highBound = 100;
	int numIndex = 50;
	while(numIndex <= highBound)
	{
		sum += numIndex;
		numIndex++;
	}
	cout<<"50--100 sum:"<<sum<<endl;
	return 0;
}
```
###练习1.10
```cpp
#include<iostream>
using namespace std;

int main(){
	int startNum = 10;
	while(startNum >= 0)
	{
		cout<<startNum<<'\t';
		startNum--;
	}
	cout<<endl;
	return 0;
}
```
###练习1.11
```cpp
#include<iostream>
using namespace std;

void sortNum(int &startNum,int &endNum)
{
	int tempNum;
	if(startNum > endNum)
	{
		tempNum = startNum;
		startNum = endNum;
		endNum = tempNum;
	}
}

int main(){
	int startNum;
	int endNum;
	cout<<"请输入整数范围的起始和结束数：";
	cin>>startNum>>endNum;

	sortNum(startNum,endNum);
	for(int i = startNum;i <= endNum;i++)
	{
		cout<<i<<'\t';
	}
	cout<<endl;
	return 0;
}
```
###练习1.14
####for和while的优缺点，区别
没有本质区别，也没有速度区别。在表达能力上二者完全等价。在机器语言的角度来看，本质都是 conditional jump. 细微的区别在于for循环和while循环会在 loop statement 前多做一次conditional jump. do_while 则不会。
###练习1.16
####cin读取不定输入，求和
####分析：最后结束cin流时是输入ctrl+z
```cpp
#include<iostream>
using namespace std;

int main(){
	int sum = 0;
	int bufferNum;
	cout<<"请输入需求和的整数：";
	while(cin>>bufferNum)
	{
		sum += bufferNum;
	}
	cout<<"sum:"<<sum<<endl;
	return 0;
}
```



