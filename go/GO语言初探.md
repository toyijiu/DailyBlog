#GO初探

##入门
*学习参考[《学习go语言》](http://mikespook.com/learning-go/)*

##介绍
- 并行，chanel，快速，安全，标准格式化，类型后置（var a int）,UTF-8，开源。
- 和erlang相比，erlang是函数式的，和C一样，go是命令式的。erlang运行在虚拟机上，go是静态编译的。go更接近于unix。

##安装
- 不说了，百度吧

Q1. (0) For-loop
1. 创建一个基于 for 的简单的循环。使其循环 10 次，并且使用 fmt 包打印出计数
器的值。

```
package main

func main(){
	maxBound := 10
	for i:=0;i<maxBound;i++{
		println(i)
	}
}
```
2. 用 goto 改写 1 的循环。关键字 for 不可使用。

```
package main

func main(){
	maxBound := 10
	index := 0
	
	LOOP:
		println(index)
		index++
		if index < maxBound{
			goto LOOP
		}
}
```

3. 再次改写这个循环，使其遍历一个 array，并将这个 array 打印到屏幕上。

```
package main

func main(){
	array := "abcdefg"
	
	for pos,char := range array{
		println(pos,":",string(char))
	}
}
```

Q2. (0) FizzBuzz
1. 解决这个叫做 Fizz-Buzz[23] 的问题：
编写一个程序，打印从 1 到 100 的数字。当是3的倍数就打印 “Fizz”代替数字，当是5的倍数就打印 “Buzz” 。当数字同时是3和5的倍数时，打印 “FizzBuzz” 。

```
package main

func main(){
	replace_three := "Fizz"
	replace_five := "Buzz"
	replace_all := "FizzBuzz"
	low_bound := 1
	high_bound := 100
	
	for i := low_bound;i <= high_bound;i++{
		if(i % 3 + i % 5 == 0){
			println(replace_all);
			continue;
		}

		if(i % 3== 0){
			println(replace_three);
			continue;
		}
		
		if(i % 5 == 0){
			println(replace_five);
			continue;
		}
	
		println(i);
	}
	
}
```

Q3. (1) 字符串
1. 建立一个 Go 程序打印下面的内容（到 100 个字符）：
A
AA
AAA
AAAA
AAAAA
AAAAAA
AAAAAAA
...

```
package main

func main(){
	
	high_bound := 100
	string := "A"

	for i := 0;i < high_bound;i++{
		println(string)
		string += "A"
	}
	
}
```

2. 建立一个程序统计字符串里的字符数量：
asSASA ddd dsjkdsjs dk
同时输出这个字符串的字节数。 提示： 看看 unicode/utf8 包。

```
package main

import "unicode/utf8"

func main(){
	
	myString := "asSASA ddd dsjkdsjs dk"
	
	charNum := utf8.RuneCount([]byte(myString))
	strLen := len([]byte(myString))
	println("string:",myString,",charNum:",charNum,",strLen:",strLen)
}
```

3. 扩展/修改上一个问题的程序，替换位置 4 开始的三个字符为 “abc”。

```
package main

func main(){
	
	myString := "asSASA ddd dsjkdsjs dk"
	charArray := []rune(myString)
	copy(charArray[4:4+3],[]rune("abc"))

	println(myString)
	println(string(charArray))
}
```

4. 编写一个 Go 程序可以逆转字符串，例如 “foobar” 被打印成 “raboof”。 提示： 不
幸的是你需要知道一些关于转换的内容，参阅 “转换” 第 59 页的内容。

```
package main

func main(){
	
	myString := "foobar"
	stringLen := len([]rune(myString))
	charArray := []rune(myString)
	
	var temp rune
	for i,j:=0,stringLen-1; i<j;i,j = i+1,j-1{
		temp = charArray[i]
		charArray[i] = charArray[j]
		charArray[j] = temp
	}
	println(string(charArray))
}
```







