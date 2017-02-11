#Haroopad 无法显示中文的解决方法

------

##问题

安装新的Haroopad后，第一次用可能会出现中文无法显示的问题。解决方法是修改其CSS文件，打开文件->偏好设置->编辑器，点击编辑按钮，修改CSS文件，将其中代码修改成如下代码

```cpp
/**
  You can only use the following style.

  - color, font-family, font-style
  - text-shadow
  - background-*

  Example:
    font-family: "微软雅黑", "Meiryo UI", "Malgun Gothic", "Segoe UI", "Trebuchet MS", Helvetica, sans-serif !important;
    text-shadow: 0 1px rgba(0, 0, 0, .8);
    background-image: url('wood.jpg');
    background-attachment: fixed;
    background-repeat: no-repeat;
    background-size: cover;
*/

editor {
  font-family: "微软雅黑", "Meiryo UI", "Malgun Gothic", "Segoe UI", "Trebuchet MS", Helvetica, sans-serif !important;
}
linenumber {
  font-family: "微软雅黑", "Meiryo UI", "Malgun Gothic", "Segoe UI", "Trebuchet MS", Helvetica, sans-serif !important;
}
activeline {
  font-family: "微软雅黑", "Meiryo UI", "Malgun Gothic", "Segoe UI", "Trebuchet MS", Helvetica, sans-serif !important;
}

/*
  You can only use the following style.

  - color, font-family, font-style
  - text-shadow

  Example:
    color: #adadad;
    font-style: bold;
    text-shadow: 0 1px rgba(0, 0, 0, .8);
*/
header {}
code {}
blockquote {}
li1 {}
li2 {}
li3 {}
hr {}
img {}
a {}
em {}
i {}
strong {}
```

