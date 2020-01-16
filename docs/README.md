#   git&github

## git 是什么

1.  Git是目前世界上最先进的分布式版本控制系统（工具）。

2.  Git是免费、开源的

3.  最初Linux和Git之父李纳斯·托沃兹（Linus Benedic Torvalds）是为辅助 Linux 内核开发的，来替代 BitKeeper

   与CVS、Subversion一类集中式版本控制工具不同，采用分布式版本库，不需要服务器端软件，就可以运作版本控制，使得源代码的发布和交流极其方便。

 

## git的特点

### 优点

1. 直接记录快照，而非差异比较

2. 近乎所有操作都是本地执行

3. 时刻保持数据完整性

4. 多数操作仅添加数据
5. 适合分布式开发，强调个体。
6. 公共服务器压力和数据量都不会太大
7. 速度快、灵活
8. 任意两个开发者之间可以很容易的解决冲突。
9. 离线工作

### 缺点

1. 模式上比SVN更加复杂。
2. 不符合常规思维。
3. 代码保密性差，一旦开发者把整个库克隆下来就可以完全公开所有代码和版本信息。

## github是什么

GIT-HUB :一个网站（开源的源代码托管平台），可以在自己的账户下创建仓库，用来管理项目源代码（源代码是基于git传到仓库中）熟知的插件、类库、框架等都在这个平台上有托管、可以下载观看和研究源码、并且开发者可以在Github上创建自己的开源项目并与其他开发者协作编码。创业公司可以用它来托管软件项目，GitHub的独特卖点在于从另外一个项目进行分支的简易性。

## 关于git与github的操作

### 1.git的全局配置

第一次安装完成git后，我们在全局环境下配置基本信息 我是谁

```  
git config -l 查看配置信息
git config --global -l 查看全局配置信息

配置全局信息，用户名和邮箱

git config --global -user.name 'xxx' 
git config --global -user.email 'xxx' 
```

###  2. 创建本地git仓库 

``` shell
$ git init  （会创建一个本地的 ".git"隐藏文件夹, 不能删除,删除不完整 ）>
```

> 在本地编写完成代码后（在工作区），把一些文件提交奥暂存区
>
> ```shell
> status：状态
> 
> $ git add  xxx 把某一个文件或者而文件夹提交到暂存区
> $ git add .  /-A  把当前仓库最新修改的文件都提交到暂存区
> $ git rm  xxx   把当前库的某一个文件从暂存区撤回
> 
> $ git status   查看当前文件的状态（红色代表在工作区、绿色代表在暂存区，看不见东西东西所有修改都已经提交到历史区）
> 
> ```

>把暂存区内容提交到历史区

```shell
commit： 提交

$ git commit -m'描述信息，本次提交内容的一个描述'
$ git log 查看历史版本
$ git reflog 包含回滚信息
```

###  3.本地仓库提交到中央仓库

```shell
remote ：远程    rm：remove 删掉去除  

首先应该建立本地仓库与远程仓库的链接
查看本地仓库与哪些远程仓库保持链接
git Remote -v
让本地仓库与远程仓库建立链接，origin是随便起的链接名，可以改成自己想要的，一般都用这
git remote add origin  git仓库链接
删除关联信息
git remote rm  origin  	
```

>   提交
>
>   提交之前最好先拉取，处理冲突

```  
$ git pull origin master
将本地代码提交到远程仓库（需要输入github的用户名密码）
$ git push origin master

```

### 4.真实项目操作流程（git clone）

```  shell
$ git clone [ 远程仓库git地址] [别名 ，可以不设置 ，默认是仓库名，前面有空格]

真实项目开发流程

1.组长或负责人创建中央仓库
2.小组成员给予$ git clone 把远程仓库及默认内容克隆到本地仓库一份
get clone 解决了三个事情（初始化本地仓库 ‘git init’、和对应的远程仓库保持挂暖‘git remote add ’、 把远程曾库默认内 
```

### 5.一个新项目的全流程

1. 创建项目文件夹

2. 把他作为一个新的仓库进行代码管理（$ git init /$ git clone  链接把远程仓库复制下来）

3. 初始化配置清单 package json --  $npm init -y

4. 安装多需要的模块：$npm  install(i) jquery  ...

5. 正常开发

6. 开发中：可能需要再本地配置命令去完成一些功能（例如less文件编译，此时需要配置npm可执行命令）

7. ``` 
   lessc css/index.less css/index .min .css）用lessc 把css下的index.less 文件 编译到 css下的文件夹的index.min.css 然后-x 压。缩
   ```

8. 开发中我们需要基于git把文件夹进行管理：生成对应的历史版本

提交到咱群去、历史区、远程仓库的时候，项目中很多文件是无需处理和提交的，例如：node_modules、idea。。。。 ，不需要提交的，我们生成一个.gitignore忽略文件



8. 由于每次git提交的时候，我们都不去提交node_modules,所以团队协作开发中，每当拉下来程序后，都需要“跑环境”：执行$ npm install ,，按照package.json script 文中 的依赖项信息，把缺失的模块都安装一遍

9.   基于yarn进行第三方模块管理，加快模块安装的速度

     ```shell
     $ npm i yarn -g  安装yarn
     cmd  $ yarn -y 生成一个package.json  
     跑环境  $yarn install
     $yarn add xxx 安装模块
     $yarn remove  xxx 删除模块
     
     
     ```

或者nrm切源提高npm速度0

   npm i nrm -g 安装 nrm
   nrm ls
   nrm use xxx

   记下来继续使用npm命令即可





##  nodejs/npm 

### 介绍

1. node.js是javascript的一种运行环境，是对Google V8引擎进行的封装。是一个服务器端的javascript的解释器。

2. nodejs中含有npm，你打开cmd输入npm -v会发现npm的版本号，npm ：node package manger ：node 模块管理工具,根据npm我们可快速安装、卸载所需要的资源文件，（例如：jquery 、vue、 vue-router）
   （其实npm是nodejs的包管理器（package manager）。我们在Node.js上开发时，会用到很多别人已经写好的javascript代码，每当我们需要别人的代码时，搜索，下载源码，解压，再使用，会非常麻烦。于是就出现了包管理器npm。大家把自己写好的源码上传到npm官网上，如果要用某个或某些个，直接通过npm安装就可以了，不用管那个源码在哪里。并且如果我们要使用模块A，而模块A又依赖模块B，模块B又依赖模块C和D，此时npm会根据依赖关系，把所有依赖的包都下载下来并且管理起来。试想如果这些工作全靠我们自己去完成会多么麻烦！）

node官网： 下载node（长期支持稳定版）、安装node后、npm也就跟着安装了

### 基于npm 进行模块管理 

http://www.npmjs.com 基于npm 是从npmjs .com平台上下载安装



```    powershell
 $  npm install xxx   把模块安装在当前项目中 （node_modules） install可简写i
 $  npm install xxx -g  把模块安装在全局环境中
 $  npm i xxx@1.0.0 安装指定版本号的模板
 $  npm view xxx  versions > xxx.versions .json 查看某个模块的版本信息（输出到指定json文件中）
 
 
 /*
 
  什么情况可以把模块安装在全局
 可以使用’命令‘对任何项目进行操作
 
 安装本地在本地项目中的模块
 --可以在没项目中导入进来使用 
 --但是默认不能给予命令（  ）来操作，因为没有cmd文件  */
 --但是可以基于package.json 中的crripts，配置一些npm的可执行的命令，然后$npm run xxx 执行
 
 $ npm init -y 初始化当前项目的配置依赖清单（项目文件夹名字中不能出现中文、大写字母和特殊符号）
 dependencies ：生产依赖模块（开发和项目部署的时候都需要）
 devdependencies：开发依赖模块（只有开发的时候需要）
 script :配置本地可执行命令（'lessc 1.less 1.min.css -x'  ）编译为css可本地文件夹执行 -x（压缩）  
 cmd  npm run less
 
 $ npm i xxx --save 把模块保存在清单生产依赖中
 $ npm i xxx --save-dev  把模板保存在清单开发依赖中
 $ npm install (跑环境 ，按照清单最新信息安装所需的最新模块（被别人更新之类的）,以package.json（配置清单（依赖和生产））里面生产模块为主)
 
 $ npm root -g 查看全局安装模块的目录  （因为安装目录下生成了xxx.cmd）文件，所以能够用命令进行操作
 $ npm uninstall xxx
 $ npm uninstall xxx-g 卸载安装过的模块
```

window操作系统：在某个文件夹下执行dos命令

1. Windows+r > 运行窗格中输入cmd

磁盘符：  进入指定磁盘 E：

​    cd xxx 进入指定目录   （cd +拖文件夹进入dos命令也可以）

2.  在文件夹地址栏直接输入cmd

3.  在文件夹中“shift+鼠标右键”- 在此处打开 命令窗口

查看当前有哪些文件  dir  

清屏  cls （clear screen）



# 计算机基础原理

## 储存原理

##  进制相关

## 。。。







# Python

## Python是什么

### 简介

Python 是一个结合了解释性、编译性、互动性并且**面向对象**的高层次脚本语言。Python 的设计具有很强的可读性，它具有比其他语言更有特色语法结构。

- **Python 是一种解释型语言：** 这意味着开发过程中没有了编译这个环节。类似于PHP和Perl语言。

- **Python 是交互式语言：** 这意味着，您可以在一个 Python 提示符 **>>>** 后直接执行代码。

- **Python 是面向对象语言:** 这意味着Python支持面向对象的风格或代码封装在对象的编程技术。

- **Python 是初学者的语言：**Python 对初级程序员而言，是一种伟大的语言，它支持广泛的应用程序开发，从简单的文字处理到 WWW 浏览器再到游戏。

  ***
  
  
  
  

### 发展历史

Python 是由 Guido van Rossum 在八十年代末和九十年代初设计出来的。

Python 本身也是由诸多其他语言发展而来的,包括 ABC、Modula-3、C、C++、Algol-68、SmallTalk、Unix shell 和其他的脚本语言等等。

像 Perl 语言一样，Python 源代码同样遵循 GPL(GNU General Public License)协议。现在 Python 是由一个核心开发团队在维护，Guido van Rossum 仍然占据着至关重要的作用，指导其进展。

***



### 特点



- **1.易于学习：**Python有相对较少的关键字，结构简单，和一个明确定义的语法，易于学习。

- **2.易于阅读：**Python代码定义的更清晰。

- **3.易于维护：**Python的成功在于它的源代码是相当容易维护的。

- **4.一个广泛的标准库：**Python的最大的优势之一是丰富的库，跨平台的，在UNIX，Windows和Macintosh兼容很好。

- **5.互动模式：**互动模式的支持，您可以从终端输入执行代码并获得结果的语言，互动的测试和调试代码片断。

- **6.可移植：**基于其开放源代码的特性，Python已经被移植（也就是使其工作）到许多平台。

- **7.可扩展：**如果你需要一段运行很快的关键代码，或者是想要编写一些不愿开放的算法，你可以使用C或C++完成那部分程序，然后从你的Python程序中调用。

- **8.数据库：**Python提供所有主要的商业数据库的接口。

- **9.GUI编程：**Python支持GUI（graphical user interface 图形化操作界面）可以创建和移植到许多系统调用。

- **10.可嵌入:** 你可以将Python嵌入到C/C++程序，让你的程序的用户获得"脚本化"的能力。

  ***

### 优点



-  **简单** -- Python 是一种代表简单主义思想的语言。阅读一个良好的 Python 程序就感觉像是在读英语一样，尽管这个英语的要求非常严格！Python 的这种伪代码本质是它最大的优点之一。它使你能够专注于解决问题而不是去搞明白语言本身。
-  **易学** -- Python 极其容易上手。Python 有极其简单的语法。
-  **免费、开源** -- Python 是 FLOSS（自由/开放源码软件）之一。简单地说，你可以自由地发布这个软件的拷贝、阅读它的源代码、对它做改动、把它的一部分用于新的自由软件中。FLOSS 是基于一个团体分享知识的概念。这是为什么 Python 如此优秀的原因之一——它是由一群希望看到一个更加优秀的 Python 的人创造并经常改进着的。
-  **高层语言** -- 当你用 Python 语言编写程序的时候，你无需考虑诸如如何管理你的程序使用的内存一类的底层细节。
-  **可移植性** -- 由于它的开源本质，Python 已经被移植在许多平台上（经过改动使它能够工作在不同平台上）。如果你小心地避免使用依赖于系统的特性，那么你的所有 Python 程序无需修改就可以在下述任何平台上面运行。这些平台包括 Linux、Windows、FreeBSD、Macintosh、Solaris、OS/2、Amiga、AROS、AS/400、BeOS、OS/390、z/OS、Palm OS、QNX、VMS、Psion、Acom RISC OS、VxWorks、PlayStation、Sharp Zaurus、Windows CE 甚至还有 PocketPC、Symbian 以及 Google 基于 Linux 开发的 Android 平台！
-  **解释性** --一个用编译性语言比如 C 或 C++ 写的程序可以从源文件（即 C 或 C++ 语言）转换到一个你的计算机使用的语言（二进制代码，即0和1）。这个过程通过编译器和不同的标记、选项完成。当你运行你的程序的时候，连接/转载器软件把你的程序从硬盘复制到内存中并且运行。而 Python 语言写的程序不需要编译成二进制代码。你可以直接从源代码运行程序。在计算机内部，Python 解释器把源代码转换成称为字节码的中间形式，然后再把它翻译成计算机使用的机器语言并运行。
-  **面向对象** -- Python 既支持面向过程的编程也支持面向对象的编程。在“面向过程”的语言中，程序是由过程或仅仅是可重用代码的函数构建起来的。在“面向对象”的语言中，程序是由数据和功能组合而成的对象构建起来的。与其他主要的语言如 C++ 和 Java 相比，Python 以一种非常强大又简单的方式实现面向对象编程。
-  **可扩展性** -- 如果你需要你的一段关键代码运行得更快或者希望某些算法不公开，你可以把你的部分程序用 C 或 C++ 编写，然后在你的 Python 程序中使用它们。
-  **丰富的库** -- Python 标准库确实很庞大。它可以帮助你处理各种工作，包括正则表达式、文档生成、单元测试、线程、数据库、网页浏览器、CGI、FTP、电子邮件、XML、XML-RPC、HTML、WAV 文件、密码系统、GUI（图形用户界面）、Tk 和其他与系统有关的操作。记住，只要安装了 Python，所有这些功能都是可用的。这被称作 Python 的“功能齐全”理念。除了标准库以外，还有许多其他高质量的库，如 wxPython、Twisted 和 Python 图像库等等。
-  **规范的代码** -- Python 采用强制缩进的方式使得代码具有极佳的可读性。

### 缺点

-  运行速度，有速度要求的话，用 C++ 改写关键部分吧。
-  国内市场较小（国内以 Python 来做主要开发的，目前只有一些 web2.0 公司）。但时间推移，目前很多国内软件公司，尤其是游戏公司，也开始规模使用他。
-  中文资料匮乏（好的 Python 中文资料屈指可数，现在应该变多了）。托社区的福，有几本优秀的教材已经被翻译了，但入门级教材多，高级内容还是只能看英语版。
-  构架选择太多（没有像 C# 这样的官方 .net 构架，也没有像 ruby 由于历史较短，构架开发的相对集中。Ruby on Rails 构架开发中小型web程序天下无敌）。不过这也从另一个侧面说明，python比较优秀，吸引的人才多，项目也多。





***



## python 基础

### 1. 基础语法与规范

#### 编码

默认情况下，Python 3 源码文件以 **UTF-8** 编码，所有字符串都是 unicode 字符串。 当然你也可以为源码文件指定不同的编码：

```
# -*- coding: cp-1252 -*-
```

#### 标识符



简单地理解，标识符就是一个名字，就好像我们每个人都有属于自己的名字，它的主要作用就是作为变量、函数、类、模块以及其他对象的名称。

Python 中标识符的命名不是随意的，而是要遵守一定的命令规则，比如说：

* 标识符是由字符（A~Z 和 a~z）、下划线和数字组成，但第一个字符不能是数字。

* 标识符不能和 Python 中的保留字相同。

* Python中的标识符中，不能包含空格、@、% 以及 $ 等特殊字符。

  

标识符的命名，除了要遵守以上这几条规则外，不同场景中的标识符，其名称也有一定的规范可循，

例如：



> 当标识符用作模块名时，应尽量短小，并且全部使用小写字母，可以使用下划线分割多个字母，例如 game_mian、game_register 等。
>
> 当标识符用作包的名称时，应尽量短小，也全部使用小写字母，不推荐使用下划线，例如 com 等。
>
> 当标识符用作类名时，应采用单词首字母大写的形式。例如，定义一个图书类，可以命名为 Book。
>
> 模块内部的类名，可以采用 "下划线+首字母大写" 的形式，如 _Book;
>
> 函数名、类中的属性名和方法名，应全部使用小写字母，多个单词之间可以用下划线分割；
>
> 常量命名应全部使用大写字母，单词之间可以用下划线分割；



在 Python 3 中，可以用中文作为变量名，非 ASCII 标识符也是允许的了。

**注意： 不要使用你需要引入的包名、类名、函数名等作为标识符 **





#### 保留字

保留字即关键字，我们不能把它们用作任何标识符名称,不能被定义。Python 的标准库提供了一个 keyword 模块，可以输出当前版本的所有关键字：

```
>>> import keyword
>>> keyword.kwlist
['False', 'None', 'True', 'and', 'as', 'assert', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
```

#### 注释

* Python中单行注释以 **#** 开头(左端加#)
* 多行注释可以用多个 **#** 号或者在开头和结尾加英文状态的三个单引号或双引号，即’’’注释内容’’’

------

#### 转义字符

*  反斜杠可以用来转义，使用r可以让反斜杠不发生转义。。 如 r"this is a line with \n" 则\n会显示，并不是换行。

#### 空行

函数之间或类的方法之间用空行分隔，表示一段新的代码的开始。类和函数入口之间也用一行空行分隔，以突出函数入口的开始。

空行与代码缩进不同，空行并不是Python语法的一部分。书写时不插入空行，Python解释器运行也不会出错。但是空行的作用在于分隔两段不同功能或含义的代码，便于日后代码的维护或重构。

**记住：**空行也是程序代码的一部分。



#### 行与缩进

python最具特色的就是使用缩进来表示代码块，不需要使用大括号 **{}** 。

*缩进的空格数是可变的，但是同一个代码块的语句必须包含相同的缩进空格数*。实例如下：

缩进相同的一组语句构成一个代码块，称之为代码组

以下代码最后一行语句缩进数的空格数不一致，会导致运行错误：

```shell
if True:
    print ("Answer")
    print ("True")
else:
    print ("Answer")
  print ("False")    # 缩进不一致，会导致运行错误
```

以上程序由于缩进不一致，执行后会出现类似以下错误：

```
 File "test.py", line 6
    print ("False")    # 缩进不一致，会导致运行错误
                                      ^
IndentationError: unindent does not match any outer indentation level
```

***

#### 同一行显示多条语句

Python可以在同一行中使用多条语句，语句之间使用分号(;)分割：

> import sys; x = 'runoob'; sys.stdout.write(x + '\n')

#### 多行语句

Python 通常是一行写完一条语句，但如果语句很长，我们可以使用反斜杠 \ 来实现多行语句，例如：

```
total = item_one + \
        item_two + \
        item_three
```

在 [], {}, 或 () 中的多行语句，不需要使用反斜杠(\)，例如：

```
total = ['item_one', 'item_two', 'item_three',
        'item_four', 'item_five']
```

### 2. 6种标准数据类型



#### 数字(Number)类型

python中数字有四种类型：整数、布尔型、浮点数和复数。

- **int** (整数), 如 1, 只有一种整数类型 int，表示为长整型，没有 python2 中的 Long。
- **bool** (布尔), 如 True和false。
- **float** (浮点数), 如 1.23、3E-2
- **complex** (复数), 如 1 + 2j、 1.1 + 2.2j

------

#### 字符串(String)

- 字符串就是放在引号里面的一系列字符。不严谨的说，就是标点符号和字母文字组成的那些单词、句子，比如：

  ```python3
  ‘hello’
  ‘My favourite number is 23’
  ```

- 一定要用引号引起来，不然就是变量名，中单引号和双引号使用完全相同。

- 引号只是告诉 Python，引号中间的内容是字符串而已，引号本身并不会真正显示出来，只有引号中的字符会显示出来。

- 单引号和双引号都可以，但是必须前后匹配，不能开始用单引号，结束用双引号。 为什么单双引号都可以呢？是为了方便很多特殊情况：比如：

  ```python3
  'What's your name?' #这样写是不对的，会报错
  ```

  上面这句话中有三个单引号，第二个应该被显示出来，但 Python 以为第二个代表字符串结束了，以为第三个单引号代表新的字符串开始，但没找到结束的单引号，所以报错。正确写法是：

  ```python3
  "What's your name?" 
  ```

  第一个和第三个双引号匹配，中间的单引号就会被 Python 认为是正常的字符显示出来了。

- 按字面意义级联字符串，如"this " "is " "string"会被自动转换为this is string。

- 字符串可以用 + 运算符连接在一起，用 * 运算符重复。

- Python 中的字符串有两种索引方式，从左往右以 0 开始，从右往左以 -1 开始。

- Python中的字符串不能改变。

- Python 没有单独的字符类型，一个字符就是长度为 1 的字符串。

- 字符串的截取的语法格式如下：**变量[头下标:尾下标:步长]**

  

  > ```
  >  str='Runoob'  
  > 
  >  print(str) # 输出字符串 
  > 
  >  print(str[0:-1])  # 输出第一个到倒数第二个的所有字符
  > 
  >  print(str[0])   # 输出字符串第一个字符 
  > 
  >  print(str[2:5])   # 输出从第三个开始到第五个的字符
  > 
  >  print(str[2:])  # 输出从第三个开始后的所有字符 
  > 
  >  print(str * 2)   # 输出字符串两次 
  > 
  >  print(str + '你好')  # 连接字符串  
  > 
  >  print('------------------------------')  
  > 
  >  print('hello\nrunoob')      # 使用反斜杠(\)+n转义特殊字符 
  > 
  >  print(r'hello\nrunoob')     # 在字符串前面添加一个 r，表示原始字符串，不会发生转义 
  > 
  >  这里的 r 指 raw，即 raw string    
  > ```
  >
  > 



------

#### 列表

它的位置或索引（下标），第一个索引是0，第二个索引是1，依此类推。

列表是最常用的Python数据类型，列表的数据项不需要具有相同的类型

创建一个列表，只要把逗号分隔的不同的数据项使用方括号括起来即可。如下所示：

``` list1 = ['Google', 'Runoob', 1997, 2000];``` 

 ``` list2 = [1, 2, 3, 4, 5 ]; ``` 

 ```list3 = ["a", "b", "c", "d"]; ```



* **Python列表脚本操作符**

列表对 + 和 * 的操作符与字符串相似。+ 号用于组合列表，* 号用于重复列表。

如下所示：

| Python 表达式                         | 结果                         | 描述                 |
| :------------------------------------ | :--------------------------- | :------------------- |
| len([1, 2, 3])                        | 3                            | 长度                 |
| [1, 2, 3] + [4, 5, 6]                 | [1, 2, 3, 4, 5, 6]           | 组合                 |
| ['Hi!'] * 4                           | ['Hi!', 'Hi!', 'Hi!', 'Hi!'] | 重复                 |
| 3 in [1, 2, 3]                        | True                         | 元素是否存在于列表中 |
| for x in [1, 2, 3]: print(x, end=" ") | 1 2 3                        | 迭代                 |

* **Python列表截取与拼接**

Python的列表截取与字符串操作类型，如下所示：

L=['Google', 'Runoob', 'Taobao']

操作：

| Python 表达式 | 结果                 | 描述                                               |
| :------------ | :------------------- | :------------------------------------------------- |
| L[2]          | 'Taobao'             | 读取第三个元素                                     |
| L[-2]         | 'Runoob'             | 从右侧开始读取倒数第二个元素: count from the right |
| L[1:]         | ['Runoob', 'Taobao'] | 输出从第二个元素开始后的所有元素                   |

列表还支持拼接操作：

``` squares = [1, 4, 9, 16, 25] ``` 

 ```squares += [36, 49, 64, 81, 100] ```

 ```squares [1, 4, 9, 16, 25, 36, 49, 64, 81, 100] ```

* **嵌套列表**

使用嵌套列表即在列表里创建其它列表，例如：

``` shell
a = ['a', 'b', 'c']
n = [1, 2, 3]
x = [a, n]
x = [['a', 'b', 'c'], [1, 2, 3]]

print(x[0])     输出  ['a', 'b', 'c']

```



* **Python列表函数&方法***

Python包含以下函数:

| 序号 | 函数                                                         |
| :--- | ------------------------------------------------------------ |
| 1    | [len(list)](https://www.runoob.com/python3/python3-att-list-len.html) 列表元素个数 |
| 2    | [max(list)](https://www.runoob.com/python3/python3-att-list-max.html) 返回列表元素最大值 |
| 3    | [min(list)](https://www.runoob.com/python3/python3-att-list-min.html) 返回列表元素最小值 |
| 4    | [list(seq)](https://www.runoob.com/python3/python3-att-list-list.html) 将元组转换为列表 |

Python包含以下方法:  （方法后面都用 （ . ）和（）链接）

| 序号 | 方法                                                         |
| :--- | :----------------------------------------------------------- |
| 1    | [list.append(obj)](https://www.runoob.com/python3/python3-att-list-append.html) 在列表末尾添加新的对象 |
| 2    | [list.count(obj)](https://www.runoob.com/python3/python3-att-list-count.html) 统计某个元素在列表中出现的次数 |
| 3    | [list.extend(seq)](https://www.runoob.com/python3/python3-att-list-extend.html) 在列表末尾一次性追加另一个序列中的多个值（用新列表扩展原来的列表） |
| 4    | [list.index(obj)](https://www.runoob.com/python3/python3-att-list-index.html) 从列表中找出某个值第一个匹配项的索引位置 |
| 5    | [list.insert(index, obj)](https://www.runoob.com/python3/python3-att-list-insert.html) 将对象插入列表 |
| 6    | [list.pop([index=-1\])](https://www.runoob.com/python3/python3-att-list-pop.html) 移除列表中的一个元素（默认最后一个元素），并且返回该元素的值 |
| 7    | [list.remove(obj)](https://www.runoob.com/python3/python3-att-list-remove.html) 移除列表中某个值的第一个匹配项 |
| 8    | [list.reverse()](https://www.runoob.com/python3/python3-att-list-reverse.html) 反向列表中元素 |
| 9    | [list.sort( key=None, reverse=False)](https://www.runoob.com/python3/python3-att-list-sort.html) 对原列表进行排序 |
| 10   | [list.clear()](https://www.runoob.com/python3/python3-att-list-clear.html) 清空列表 |
| 11   | [list.copy()](https://www.runoob.com/python3/python3-att-list-copy.html) 复制列表 |

元组

字典

集合