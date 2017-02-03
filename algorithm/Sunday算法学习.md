#Sunday算法学习
>判断字符串是否包含的算法，效率比KMP高，而且更加浅显易懂。
>学习自[yangfan876@126的博客](http://blog.163.com/yangfan876@126/blog/static/80612456201342205056344/)。非常感谢~

![图片](http://img.blog.csdn.net/20160421233419706)

i，j两个指针分别从头开始匹配，当发现不匹配时，判断子串的后一位对应母串中的字符（上面的例子就是空格，k所在位置）在子串中是否存在（子串要从后向前匹配）。存在的话两位置对齐，再从头开始匹配，如果不存在就将子串整体后移，和母串k+1处的字符对齐，重新匹配，直到找到或者母串遍历完。

```
//得到字符在母串中的位置，从后往前算,未找到返回-1
int getWordLocation(char word,char* srcString)
{
	int foot = strlen(srcString) - 1;
	while(srcString[foot] != '\0')
	{
		if(word == srcString[foot])
		{
			return (strlen(srcString) - foot);
		}
		foot--;
	}

	return -1;
}

int sunday(char* srcString,char* subString)
{
	//合法性判断
	if(srcString == NULL || subString == NULL)
	{
		return -1;
	}

	int srcLength = strlen(srcString);
	int subLength = strlen(subString);
	int subPoint = 0;
	int srcPoint = 0;
	int pos = 0;
	while(srcPoint < srcLength)
	{
		subPoint = 0;
		while(subString[subPoint] == srcString[srcPoint + subPoint] && subString[subPoint] != '\0')
		{
			subPoint++;
			continue;
		}

		//完全匹配
		if(subString[subPoint] == '\0')
		{
			cout<<"get the location:"<<srcPoint<<"--"<<srcPoint + subLength - 1<<endl;
			return srcPoint;
		}

		//未完全匹配，找子串后一个对应母串字母在子串位置
		if((pos = getWordLocation(srcString[srcPoint + subLength],subString)) != -1)
		{
			srcPoint += pos;
		}
		else
		{
			srcPoint += (subLength + 1);
		}
	}

	return -1;
}
```