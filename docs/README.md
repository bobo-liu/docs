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

