# 关于编程 | About Coding
## 一、什么是编程？
编程，就是“编写程序”。那么什么是程序？又怎样编写？这是我们要回答的两个核心问题。
### 1. 什么是程序？
程序，**是计算机执行的一串指令，用以完成某一项特定的任务**。具体举例来说，运行在计算机、手机等设备上的浏览器、QQ、微信等软件都属于程序。观察这些程序，它们有这样的共同特征：
- 它们与常见的文本文档格式(.txt)不同、是一种**人们不易看清而计算机可解读的一连串数字的格式。**
- **在Windows系统上，应用程序的常见后缀名是.exe**。例如msedge.exe，QQ.exe，Weixin.exe等等。
- 在GNU/Linux系统上，应用程序通常不具有后缀名，是纯粹的二进制文件(file)。在手机运行的Android、iOS系统上，应用程序通常是一个包(bundle)，而不是单独的文件。
- **但不论是怎样的操作系统，应用程序的一个重要特征是很难像文本文档一样直接读取和编辑内容。**
![Windows系统上的常见应用程序.png](http://huajidawang.asia/wp-content/uploads/2025/09/AboutCoding_1.png)
### 2. 何为编写？
编写程序，就像在Word软件里写下一篇文稿一样，就是**要从0开始“造”出一个程序**。

正如前文所说，程序的重要特征是难读取、难编辑。那么为什么我们又可以“编写”程序？**这里涉及到源码(Source Code)和编译(Compile)的概念。**

在我们接触编程的时候，我们所能够直接编写的文件，是**源码**，根据编程语言的不同，源码文件有不同的后缀名，如C语言的源码文件是.c，C++语言是.cpp(C-Plus-Plus)，Python语言是.py等等。**源码是我们能够直接阅读、编写的文字，这些文字遵循特定编程语言的语法，并确定我们最终“造”出的程序的功能。**

从源码到程序，需要一个将源码转化为程序的工具。**这个过程叫做编译，这样的工具叫做编译器(Compiler)**。

最初的编译器只具有编译的功能，与编写源码这项重要任务是割裂开的。**现代编译器已经发展成了集成开发环境(IDE, Integrated Develepment Environment)**，如初学C/C++语言常用的Dev-C++、具有强大项目管理功能的Visual Studio C++、JetBrain's IntelliJ系列等等。

作为集成开发环境的现代编译器，**集成了源码编写、调试、编译、运行、代码补全、项目管理等多重功能**。是需要学会使用的编程利器。

刚开始学习编程，比起像“造”出一个微信或QQ这样的任务来说，我们所编写的程序很简单，例如实现一个类似计算器的加法功能、把一串字符倒过来输出、给一堆数字排个序等等。

在最初学习的一段时间里，我们会长时间接触一个黑框框，这是因为我们的程序没有**图形界面**，只能显示成一个黑框框，它具有最基本的输出（程序在其中显示字）和输入（用户，也就是在电脑前的我们，在其中打字）的功能。**这个黑框框叫终端(Terminal)。**

## 二、Dev-C++的使用
Dev-C++原生支持简体中文。其设置在顶部工具栏 `工具|Tools > 环境设置|Environment Options > 基本|General > 语言|Language`。
![Dev-C++的程序界面](http://huajidawang.asia/wp-content/uploads/2025/09/AboutCoding_2.png)

在顶部工具栏的稍下方，Dev-C++提供了众多常用功能的快捷按钮。

### 1.新建文件
![新建文件](http://huajidawang.asia/wp-content/uploads/2025/09/AboutCoding_4.png)
- 单击快捷按钮的第一个图标![新建文件图标](http://huajidawang.asia/wp-content/uploads/2025/09/AboutCoding_3.png)
- 或使用`Ctrl+N`
- 或在顶部工具栏`文件|File > 新建|New > 源代码|Source File`
来新建一个源码文件。

### 2.编译与运行
![编译与运行](http://huajidawang.asia/wp-content/uploads/2025/09/AboutCoding_5.png)

在至少打开着一个源码文件的情况下：
- 单击快捷栏按钮的![编译图标](http://huajidawang.asia/wp-content/uploads/2025/09/AboutCoding_6.png)
- 或使用`F9`
- 或在顶部工具栏`文件|File > 运行|Execute > 编译|Compile`
来编译当前的源码文件。

- 单击快捷栏按钮的![运行图标](http://huajidawang.asia/wp-content/uploads/2025/09/AboutCoding_7.png)
- 或使用`F10`
- 或在顶部工具栏`文件|File > 运行|Execute > 运行|Run`
来运行运行编译好的程序

- 单击快捷栏按钮的![编译与运行图标](http://huajidawang.asia/wp-content/uploads/2025/09/AboutCoding_8.png)
- 或使用`F11`
- 或在顶部工具栏`文件|File > 运行|Execute > 编译运行|Compile & Run`
来直接编译并运行当前的源码文件。

值得说明的是，**编译是对当前保存的源码文件进行操作**。因此首次编写源码文件尚未保存的时候，进行编译会强制要求保存源码文件。
如果对已经保存的源码文件产生了更改，但没有保存更改的内容，此时进行编译时，**Dev-C++会先自动保存更改的内容，再编译**。
> 一些历史悠久的编译器版本可能不会这样做，因此经常保存、确定进行编译的源码是最新编辑的，是重要的。