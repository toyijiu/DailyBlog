#error LNK1104: 无法打开文件“msvcprtd.lib” 的问题定位解决
------

##问题现象
- 最近在看C++ Primer 第五版，需要C++11的支持，随即安装了下VS2015，安装后再编译时出现error LNK1104: 无法打开文件“msvcprtd.lib”的问题

------

##解决方法
- 通过everything查找发现msvcprtd.lib在我的电脑目录D:\VS2010\VC\lib中存在的，所以在Project->Project Property->Linker下的General的Additional Library Directories栏中添加对应lib路径吗
- 在对应的Input栏中的Additional Dependencies栏中添加msvcprtd.lib
- 问题解决