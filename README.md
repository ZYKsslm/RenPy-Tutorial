# Ren'Py：从入门到入坟

## 目录

- [Ren'Py：从入门到入坟](#renpy从入门到入坟)
  - [目录](#目录)
  - [在开始之前](#在开始之前)
    - [说明](#说明)
    - [前言](#前言)
  - [初识Ren'Py](#初识renpy)
    - [了解Ren'Py](#了解renpy)
      - [简介](#简介)
      - [Ren'Py能干什么](#renpy能干什么)
      - [Ren'Py支持加载的文件格式](#renpy支持加载的文件格式)
    - [配置](#配置)
      - [安装SDK](#安装sdk)
      - [安装IDE](#安装ide)
      - [配置Ren'Py启动器](#配置renpy启动器)
      - [基本操作](#基本操作)
    - [准备学习](#准备学习)
      - [熟悉Python很重要](#熟悉python很重要)
    - [预备知识](#预备知识)
      - [Ren'Py项目结构](#renpy项目结构)
      - [rpy脚本文件](#rpy脚本文件)
      - [rpyc可执行程序](#rpyc可执行程序)
      - [关键字（keyword）](#关键字keyword)
      - [缩进](#缩进)
  - [Ren'Py语法](#renpy语法)
    - [注释（comment）](#注释comment)
    - [给变量赋值](#给变量赋值)
      - [define语句](#define语句)
      - [default语句](#default语句)
    - [脚本标签（label）](#脚本标签label)
      - [label语句](#label语句)
      - [call语句](#call语句)
      - [jump语句](#jump语句)
      - [return语句](#return语句)
        - [携带返回值](#携带返回值)
        - [标签穿透](#标签穿透)
      - [特殊标签名](#特殊标签名)
      - [全局（global）与本地（local）脚本标签](#全局global与本地local脚本标签)
    - [对话呈现](#对话呈现)
      - [say语句](#say语句)
      - [特殊文本样式](#特殊文本样式)
      - [_函数](#_函数)
      - [角色（Character）对象](#角色character对象)
    - [图像（image）](#图像image)
      - [image语句](#image语句)
      - [show语句](#show语句)

## 在开始之前

### 说明

作者：`ZYKsslm`

E-mail：`3119964735@qq.com`

参考致谢：

1. [Ren'Py官方网站](https://renpy.org/)
2. [Ren'Py中文网](https://www.renpy.cn/)
3. [Ren'Py简中说明文档](https://www.renpy.cn/doc/)
4. [Ren'Py项目开源仓库](https://github.com/renpy/renpy)

### 前言

身为Python的忠坚用户兼开发者之一，Ren'Py于我而言毫无疑问是极具魅力的。在初识Ren'Py时，我就被其易于上手、跨平台性强等特点深深吸引，它无疑是我心目中最适合用以制作视觉小说或是Galgame的一个强大实用的开源游戏引擎。

我同时也是视觉小说一类游戏的忠实爱好者，很庆幸PyTom大佬能够用Python开发出如此一个极具魅力的游戏引擎，这让更多游戏开发者能够写出高效的代码并且专注于游戏设计。我相信，这样一来将会有更多优秀的作品问世。

在学习并使用了Ren'Py一段时间以后，我就发现一个惨痛的事实——目前Ren'Py的国内社区还并不完善，远远无法和其他游戏引擎相比。我相信各位都有这种经历：经常发现自己看不懂文档、有时候发现问题把文档亦或是论坛翻遍也没得出自己想要的结果，然后疲于在茫茫网络中苦苦寻找。我相信这对于绝大多数开发者来说可以是致命的。所以，一个想法不由而生：制作一份更加详细、易懂、系统的教程来帮助更多初学者入门Ren'Py，最终能够自己独立制作一款游戏（程序）；帮助更多Ren'Py开发者写出更加严谨、细致、高效的代码。而且这对于我来说也是一个不小的挑战，在编写这份教程的同时，我也在与你们一起学习。

本人并非专业游戏开发者，犯错在所难免。但是欢迎提出指正，我定会裨补缺漏，为Ren'Py社区尽一份绵薄之力。同时希望大家能够相互促进、共同学习，一起将Ren'Py社区建设得更加完善！————笔者

## 初识Ren'Py

>合抱之木，生于毫末；百丈之台，起于垒土；千里之行，始于足下。——《老子》

### 了解Ren'Py

#### 简介

可以说，Ren'Py天生就是为视觉小说类游戏而生的。

Ren'Py视觉小说引擎是一款开放源代码的自由软件引擎，用来创作通过电脑叙述故事的视觉小说。Ren'Py之名是Ren'ai与Python两词混合而成。Ren'ai为日文，意指“恋爱”，而Python是Ren'Py所使用的语言环境。
——*[摘自Ren'Py中文社区](https://www.renpy.cn/thread-2-1-1.html)*

简而言之，Ren'Py就是一个能够帮助我们进行游戏开发的工具，能够让我们达到事半功倍的效果。

**且Ren'Py使用超高自由度的MIT协议开源。**

意思是你可以随意使用Ren'Py引擎，无需向任何人申请，但要自己承担可能会引起的风险。

#### Ren'Py能干什么

Ren'Py几乎支持所有视觉小说所应该具有的功能，包括分支故事、存储和加载游戏、回退到之前故事的存储点、多样性的场景转换等。Ren'Py拥有类似电影剧本的语法，并且能够允许高级用户编写Python代码来增加新的功能。除此之外，游戏引擎内附的出版工具能够为脚本加密以及压缩游戏素材以防止盗版。
——*[摘自Ren'Py中文社区](https://www.renpy.cn/thread-2-1-1.html)*

也就是说，我们不必再去从头开始搭建一个GUI游戏界面，并去实现繁琐的基础功能或搭建框架，这些Ren'Py都会提供给我们，我们只管专心游戏设计就好。

我们前面提到过跨平台性，跨平台意指只需写一次代码，程序就能在多个不同的环境（操作系统）中运行，大大节省了我们的时间，提高了开发效率。基于Python的特性，目前Ren'Py支持的平台有Windows、Linux、Mac OS X、Android和iOS以及不太常用的Web前端（浏览器）。

![platforms](images/platforms.jpg)

#### Ren'Py支持加载的文件格式

在游戏制作中，我们常常需要有立绘、音频、视频等元素来丰富游戏。

我们可以让Ren'Py加载资源文件，但是Ren'Py支持渲染的图像或播放的音频的文件格式是有限制的，支持的文件格式具体如下：

- 视频格式
  - VP9
  - VP8
  - Theora
  - MPEG 4 part 2 (包括Xvid和DivX)
  - MPEG 2
  - MPEG 1
  - AV1

- 图片格式
  - BMP
  - PNG
  - JPG
  - JPEG
  - GIF
  - AVIF
  - SVG

- 音频格式
  - OPUS
  - Vorbis
  - MP3
  - MP2
  - PCM

- 容器格式：
  - WebM
  - Matroska
  - Ogg
  - Avi
  - 多种MPEG格式流媒体
  
  （注意某些格式可能需要专利许可证书。没有把握的情况下，推荐使用VP9、VP8或者Theora、Opus、Vorbis，以及WebM、Matroska或者Ogg。）

### 配置

如果你已经配置好了开发环境，那么可以跳过这一章节。

>[附官方简中文档同步章节](https://www.renpy.cn/doc/quickstart.html)

#### 安装SDK

SDK即为Software Development Kit（软件开发工具包），用于给开发者提供开发工具，就是Ren'Py本体。安装完SDK我们就可以使用Ren'Py来运行我们编写的脚本代码了。

SDK在[Ren'Py官方网站](https://renpy.org/latest.html)下载最新版即可。

#### 安装IDE

IDE即为Integrated Development Environment（集成开发环境），是用于提供程序开发环境的应用程序，一般包括代码编辑器、编译器、调试器和图形用户界面等工具。一款优秀的IDE可以让我们更高效地开发。

在支持Ren'Py开发的IDE中，我们选择微软的开源免费的代码编辑器Visual Studio Code。轻便、高效、舒适。

我们可以在[vscode官网](https://code.visualstudio.com/)中找到与自己操作系统对应的版本下载安装。

![vsocode](images/vscode.jpg)

安装完成后，我们打开vscode，打开扩展商店搜索`renpy`并下载Ren'Py扩展插件（图示第一个）。

![addition_renpy](images/addition_renpy.jpg)

#### 配置Ren'Py启动器

打开Ren'Py启动器，进入设置，点击 *文本编辑器*，选择 *Visual Studio Code（操作系统）*，这样，刚才安装的vscode就成了我们的默认文本编辑器了。

![default_ide](images/default_ide.jpg)

#### 基本操作

1. 点击 *创建新项目* 以创建一个新项目。

2. 点击 *启动项目* 以运行一个项目。

3. 点击 *打开项目* 以使用默认文本编辑器打开项目目录。

详细使用请参考官方文档。

![launcher](images/launcher.png)

### 准备学习

#### 熟悉Python很重要

由于Ren'Py是基于Python的，所以有很多概念和语法都和Python相似甚至是一样。

**因此我们强烈建议所有Ren'Py使用者都掌握Python基础**。

如果你已经熟练掌握Python，那么相信学习Ren'Py对你来说并不是什么难事，甚至只是相当于学习一个第三方库而已。所以，先熟悉Python将会使你的Ren'Py学习之路更加平坦。本教程会涉及一些Python内容，进行更加细致的讲解。

如果你是零基础，那么推荐你去一些视频网站（如 *Bilibili*）找Python相关视频学习，。

对于Python知识的要求：掌握Python的基本数据类型、流程控制语句、常用的内建函数以及基本的面向对象编程思想。

### 预备知识

#### Ren'Py项目结构

>[附官方简中文档同步章节](https://www.renpy.cn/doc/language_basics.html#base-directory)

Ren'Py项目目录分为 *基础目录* 和 *游戏目录*。

**基础目录**即为以创建项目时输入的项目名为名的目录，一般用于存放与游戏本体无关的文件如 *LICENSE* 和 *README* 等。

**游戏目录**即为位于基础目录下的名为 *game* 的目录，用于存放游戏资源和脚本文件等。

一个标准的Ren'Py项目目录结构同时也是项目的初始目录结构应如下所示：

- Project
  - log.txt
  - game
    - audio
      - ......
    - fonts
      - ......
    - gui
      - ......
    - images
      - ......
    - saves
      - navigation.json
      - persistent
    - tl
      - common.rpym
      - ......
    - gui.rpy
    - gui.rpyc
    - options.rpy
    - options.rpyc
    - screens.rpy
    - screens.rpyc
    - script.rpy
    - script.rpyc
    - SourceHanSansLite.ttf
    - ......
  - ......

*Project* 即为你的项目目录也是基础目录，基础目录下的 *game* 目录即为你的游戏目录。

#### rpy脚本文件

[附官方简中文档同步章节](https://www.renpy.cn/doc/language_basics.html#files)

游戏目录中后缀名为 *rpy* 的文件就是Ren'Py的脚本文件，用于编写脚本代码。你可以直接在里面编写代码或是自己创建脚本文件。脚本文件可以有一个或多个。

一个rpy脚本文件的文件名应遵守如下命名规范：

- 规范格式
  - 全小写并使用下划线，如：`this_is_an_example`
  - 使用驼峰命名法，如：`thisIsAnExample`

- 具有意义

- 开头不包含数字

另外，在游戏启动时，Ren'Py会读取游戏目录下（包括子目录）的所有脚本文件，它们都会被扫描并组合成整个游戏的脚本。

那么就意味着：

1. 所有脚本文件中定义的变量都能够被跨文件访问。若你在一个脚本文件中定义了变量 *var* ，那么在任意一个脚本文件中都能够访问变量 *var*。
2. 所有脚本文件中的变量均不能重名。

所以，你既可以将所有代码都写进一个脚本文件中，也可以根据分类写成多个脚本文件，但要注意变量名不能冲突。

#### rpyc可执行程序

后缀名为 *rpyc* 的文件是同名rpy脚本文件编译后的二进制可执行程序。

因为计算机是无法看懂我们的代码的，所以在我们每次编写完代码重启Ren'Py时，会自动生成或更新rpyc文件，再次运行时会直接运行rpyc文件让CPU执行。

在没有rpy文件而有rpyc文件的情况下，游戏依然能够运行其功能，但是最好不要删除rpy文件，因为可能会发生意料之外的错误。

#### 关键字（keyword）

>[附官方简中文档同步章节](https://www.renpy.cn/doc/language_basics.html#elements-of-statements)

关键字，也叫关键词。

关键字是一个英文单词，必须在游戏脚本中合法出现。这些关键字是保留字，不能用作变量名、标签名或任何其他标识符。

Ren'Py中关键字的概念跟Python中的一样。

常见的Ren'Py关键字有：
**True、False、None、if、else、elif**等。

#### 缩进

>[附官方简中文档同步章节](https://www.renpy.cn/doc/language_basics.html#block)

如果你学过Python，那么你一定清楚地明白缩进的重要性。Ren'Py与Python一样，使用缩进来表示代码的逻辑。

这里就不再赘述了。

---

那么，在进行完所有的前置准备后，我们就要开始正式学习Ren'Py语法了。

## Ren'Py语法

>问渠那得清如许？为有源头活水来。——朱熹《观书有感 • 其一》

### 注释（comment）

>[附官方简中文档同步章节](https://www.renpy.cn/doc/language_basics.html#comment)

对于程序员来说，写注释是一个重要的习惯。注释用于代码解释或功能提示等，且不会被执行。

好的注释能够让你的代码更加简洁易懂，让你的思路更加清晰，也可以让你日后或别人再看代码时不至于一头雾水。

在Ren'Py中，我们使用符号`#`放在一条语句的**开头**来表示一条注释。注释可以放在任何位置，但不能插在一条代码中间，我们一般置于代码的上一行或末尾。

如：

```renpy
# 定义角色对象
define s = Character(name=_("Sylvie"))

s "I'm Sylvie." # 希尔薇发言
```

### 给变量赋值

#### define语句

define语句用于在初始化阶段给一个变量赋值，**用define定义的变量会被当作一个常量，不应被修改。且用define定义的变量在存档时不会被保存**。

>define语句会计算其自身的表达式，并声明为一个给定的变量名。若define语句不在init语句块中，其会自动以与初始化相同的最高优先级运行。

我们使用`define`关键字、一个变量名和一个赋值号来給一个变量赋值。

```renpy
define s = Character(name=_("Sylvie"))
```

#### default语句

default语句用于给一个在游戏初始化时未定义的变量赋值。**所有用default定义的变量在存档时都会被自动保存**。

我们使用`default`关键字、一个变量名和一个赋值号来給一个变量赋值。

```renpy
default point = 10
```

### 脚本标签（label）

>[附官方简中文档同步章节](https://www.renpy.cn/doc/label.html#)

#### label语句

Ren'Py中所有的游戏流程代码都会分别写进数个脚本标签中。脚本标签类似于Python中的函数，用于跳转或调用。但不同的是，在Ren'Py中，写代码时脚本标签可以在定义前调用（函数定义总会优先运行）。

我们使用`label`关键字来定义一个脚本标签，然后是标签名，后面可紧跟一对小括号以添加参数，若没有参数则括号可以省略，最后别忘了加冒号并换行缩进。参数的写法与作用域等与Python函数完全相同。

```renpy
label sample_label(content):

  "[content]"

  return
```

#### call语句

call语句用于让主控流程进入某一脚本标签中，并在执行完这次调用后，回到原本调用的位置。

我们在脚本标签中使用关键字`call`来实现跳转，后面接一个标签名，表示让主控流程进入指定的脚本标签中。若指定的脚本标签要传入参数，则在标签名后紧跟一对小括号以传参。传参方式与Python函数传参方式完全相同。

```renpy
label start:

  "游戏开始"

  call sample_label("HelloWorld!")

  "游戏结束"

  return


label sample_label(content):

  "[content]"

  return
```

在上面的代码中，游戏开始后主控流程会先进入 *start* 标签，并在对话框中显示`游戏开始`，然后调用 *sample_label* 标签并传入字符串`HelloWorld!`作为参数，随后进入 *sample_label* 标签，并在对话框中显示`HelloWorld!`，最后返回 *start* 标签在对话框中显示`游戏结束`并返回游戏主菜单。

#### jump语句

jump语句用于让主控流程进入某一脚本标签中，并顺势执行下去。

我们在脚本标签中使用关键字`jump`来实现跳转，后面接一个标签名，表示让主控流程进入指定的脚本标签中。注意：**jump语句中指定的脚本标签不能传参。**

但你可以给指定的脚本标签添加默认值参数：

```renpy
label start:

  "游戏开始"

  jump sample_label

  "游戏结束"

  return


label sample_label(content="HelloWorld!"):

  "[content]"

  return
```

在上面的代码中，主控流程进入 *sample_label* 标签时没有给予参数，于是参数 *content* 便使用默认参数值——字符串`HelloWorld!`，随后在对话框中显示`HelloWorld!`，并直接返回游戏主菜单。

#### return语句

return语句标志着一段标签代码块的结束。

我们使用关键字`return`来结束一个脚本标签。

##### 携带返回值

在return语句后加上一个变量名还可以返回这个变量名的值，值储存在变量 *_return* 中。

```renpy
label start:

  "游戏开始"

  call sample_label(8)

  "[_return]"

  return


label sample_label(content):

  # 等价于 $ content = content + 1
  $ content += 1

  return content
```

在上面的代码中，我们调用 *sample_label* 标签并传入参数整数8，随后 *content* 参数也就是整数8自增变成9，然后返回 *start* 标签并携带返回值 *content*，此时 *content* 的值储存在变量 *_return* 中，在对话框中输出 *_return* 的值显示为9。

##### 标签穿透

Ren'Py特性：在一个脚本标签结束后如果没有添加return语句，且下面还有其它脚本标签，则主控流程将直接进入下面的脚本标签，一直到遇到return语句才结束。若下面所有的脚本标签都没有添加return语句则会一直进入到最后一个脚本标签才结束。另外这也可能会造成奇怪的错误。

笔者习惯将其称之为 *标签穿透*。

任何脚本标签结束后都应添加return语句，不然将造成标签穿透。

~~Ren'Py脚本标签结束不加return语句就像java中switch case不加break。~~

```renpy
label start:

  "游戏开始"

  call label_1

  "游戏结束"

  return

label label_1:

  "label 1"

label label_2:

  "label 2"

label label_3:

  "label 3"
```

在上面的代码中，我们调用 *label_1* 标签，进入 *label_1* 标签后在对话框显示`label_1`，随即穿透到 *label_2* 标签，进入 *label_2* 标签后在对话框显示`label_2`，随即穿透到 *label_3* 标签，进入 *label_3* 标签后在对话框显示`label_3`，然后返回 *start* 标签，在对话框显示`游戏结束`，最后返回主菜单。

**可见，任何在脚本标签结束后不添加return语句的行为都是危险的！**

#### 特殊标签名

一些标签名有特殊的作用，如控制主控流程。常见的特殊标签名有以下这些：

- start
  - 默认情况下，Ren’Py在游戏启动后会跳转至这个标签。

- quit
  - 若该标签存在，当用户退出游戏时该标签内容会被调用。

- after_load
  - 若该标签存在，当游戏读档后会调用这个标签内容。其可能被用于游戏内容更新后的数据修复。

- splashscreen
  - 若该标签存在，游戏首次运行时，在主菜单出现前，该标签内容会被调用。

- before_main_menu
  - 若该标签存在，在主菜单出现前，该标签内容会被调用。

#### 全局（global）与本地（local）脚本标签

Ren'Py中共有两种脚本标签：**全局脚本标签**与**本地脚本标签**。我们一般用的就是全局脚本标签。

全局脚本标签在所有脚本文件中通用，不能重名；而本地脚本标签则可以重名，但是需要关联一个全局脚本标签。

在定义本地脚本标签时，我们只需要在标签名前添加一个`.`即可，表示这是一个本地脚本标签而非全局脚本标签，它会与上面最近的一个全局脚本标签自动关联。

全局脚本标签与本地脚本标签有以下关系：

1. 一个本地脚本标签只能关联一个全局脚本标签，而一个全局脚本标签可以关联多个本地脚本标签。
2. 在一个全局脚本标签中可以直接访问与之关联的本地脚本标签，而想要访问其它全局脚本标签关联的本地脚本标签则需要使用 *全局脚本标签名.本地脚本标签名* 的形式来访问。
3. 在一个本地脚本标签中可以直接访问与之关联同一个全局脚本标签的另一本地脚本标签，而想要访问其它全局脚本标签关联的本地脚本标签依然需要使用 *全局脚本标签名.本地脚本标签名* 的形式来访问。

其实，它们的关系类似于类与属性~~主仆~~的关系。

下面有一段很好的例子：

```renpy
label start:

  "这是全局脚本标签start，游戏从这里开始"

  call .local_label_1

  call global_label.local_label_1

  return

label .local_label_1:

  "这是本地脚本标签.local_label_1，关联start全局脚本标签"

  call .local_label_2

  return

label .local_label_2:

  "这是本地脚本标签.local_label_2，关联start全局脚本标签"

  return
  
label global_label:

  "这是全局脚本标签global_label"

  return
  
label .local_label_1:

  "这是本地脚本标签.local_label_1，关联global_label全局脚本标签"

  call .local_label_2

  return

label .local_label_2:

  "这是本地脚本标签.local_label_2，关联global_label全局脚本标签"

  call start.local_label_2

  return
```

在上面的代码中，有 *start* 和 *globel_label* 全局脚本标签，其分别关联了 *.local_label_1* 和 *.local_label_2* 本地脚本标签。

### 对话呈现

>[附官方简中文档同步章节](https://www.renpy.cn/doc/dialogue.html#)

#### say语句

文本剧情是视觉小说类游戏的根本，一切游戏形式都要建立在对话之上。Ren'Py为我们提供了简便快捷的say语句来方便演示对话。

say语句一般有以下几种形式：

1. 一个单一字符串，表示显示的内容。一般用作旁白。
2. 由两个字符串组成，前面的字符串表示发言人的名字，后面的则是显示的内容。
3. 有些say语句会在原有基础上加上一个 *with* 从句，`with`后跟上一个转场（transition）来达到过渡效果。
4. 表示显示的内容的字符串用三引号引起，方便显示长段文本。
5. 由一个角色（Character）对象和一个字符串组成，角色对象控制发言展现的形式，字符串则是显示的内容。这种形式也是最为常用的。

```renpy
label start:

  "我很紧张"

  "我" "我喜欢你！"

  "希尔薇" "这是真的吗？！" with vpunch

  return
```

我们先讨论前三种形式。看到上面的代码，会先输出`我很紧张`，而后再以“我”的发言状态输出`我喜欢你！`，对话框的左上角有一个发言人的名字`我`，最后再以“希尔薇”的发言状态输出`这是真的吗？！`同时伴有窗口抖动效果。

*vpunch* 是一个内置转场，在with语句中可以达到让窗口抖动的效果。同时，Ren'Py还内置了很多如 *vpunch* 的转场，可以在[官方文档](https://www.renpy.cn/doc/transitions.html#pre-defined-transitions)中查看。

#### 特殊文本样式

>[附官方简中文档同步章节](https://www.renpy.cn/doc/text.html#)

所有在Ren'Py中以字符串形式呈现的文本都可以使用特殊的样式，下面将介绍一些常用的特殊样式、使用方法以及注意事项。

##### 转义符

如果你想在文本中呈现：`\`、`{`、`}`、`'`、`"`中的任意字符都需要使用转义符`\`来转义防止Ren'Py误解我们的意思。

如果你的字符串是以一对双引号表示的，那么如果你想在文本中显示双引号就需要使用转义符；如果你的字符串是以单引号表示，那么则反之。

```renpy
label start:

  "\"你好。\""
  '\'我是......\''

  return
```

同时，你还能使用`\n`来表示换行：

```renpy
label start:

  "1\n2\n3\n4"

  return
```

##### 内插字符

Ren'Py支持在文本中插入一个变量并显示变量的值，我们叫做内插字符。在Python中也有类似的字符串格式化用法。

我们使用一对方括号来修饰我们的变量。

```renpy
define s = Character(name=_("Sylvie"))

label start:

  default point = 1
  s "我的名字是[s.name]"
  "当前好感度为[point]"

  return
```

同时，内插字符还支持一些特殊转换标记。我们使用感叹号`!`来表示后面的字符为特殊转换标记。下面是一些比较常用的转换标记：

- `!i`表示在字符串中进行二次插值

```renpy
define s = Character(name=_("Sylvie"))

label start:

  default point = 100
  default introduction = "名字为[s.name]，好感度为[point]"

  s "[introduction!i]"

  return
```

- `!u`会强制把英文文本转换成大写。
- `!l`会强制把英文文本转换为小写。
- `!c`会强制把英文文本首字母转换为大写。

我们可以配合一起使用：

```renpy
define s = Character(name=_("Sylvie"))

label start:

  default content = "hello WORLD!"

  # 使用顺序不分先后，等价于s "[content!cl]"
  s "[content!lc]"

  return
```

##### 文本标签（tag）

如果你使用过HTML，那么你一定对“标签”很熟悉！在Ren'Py中，我们采用文本标签来实现对文本的特殊效果。

文本标签由一对大括号和一个标签名以及相应参数组成，不同的标签名及参数有不同的效果。

所有文本标签都需要闭合，其中有些文本标签是自闭和的，而有些文本标签需要对应的闭合标签来闭合。标签闭合间的文本将会呈现特殊效果。一般来说，文本标签的格式为：

```renpy
"{tag=arg}text{/tag}"
```

其中`tag`为标签名，`arg`为参数值，`{/tag}`为闭合标签

还有一些格式为：

```renpy
"text{tag=arg}"
```

让我们来看看实际应用。

- 锚点标签`a`

  没错，正如其名，锚点标签的作用就是“传送”，能够引导玩家进入不同的地方。它拥有多个参数，下面来一一介绍：

  - jump

    当入参为`jump`时，会进入其冒号后指定的脚本标签，类似于[*jump语句*](#jump语句)

    ```renpy
    label start:

      "点{a=jump:dianwo}我{/a}进入"

      return

    label dianwo:

      "已进入"

      return
    ```

  - call

    当入参为`call`时，会调用其冒号后指定的脚本标签，类似于[*call语句*](#call语句)

    ```renpy
    label start:

      "点{a=call:dianwo}我{/a}进入"

      "出来了"

      return

    label dianwo:

      "已进入"

      return
    ```
  
  - show

    当入参为`show`时，会显示其冒号后指定的界面，这里涉及到一个新的概念“界面”，我们不展开讨论。

  - URL

    当入参部分是一个URL（或者说网站链接）时，会自动启动浏览器打开链接。

    ```renpy
    label start:

    "{a=https://www.bilibili.com/video/BV1uT4y1P7CX/}点我涩涩{/a}"

    return
    ```

- alpha

  alpha文本标签指定一个透明度，渲染范围为自身及其闭合标签内的文本。透明度是一个介于0.0和1.0之间的数值，分别对应完全透明和完全不透明。

  ```renpy
  label start:

    "{alpha=0.8}总觉得......{/alpha}"
    "{alpha=0.5}要消失了呢......{/alpha}"
    "{alpha=0.3}......{/alpha}"

    return
  ```

- b
  
  粗体标签，将自身及其毕业标签内的文本渲染为粗体。

- i

  斜体标签将自身及其闭合标签之间的文本渲染为斜体。

- s

  删除线标签在其自身及其闭合标签之间的文本上画一条删除线。

- u

  下划线标签在其自身及其闭合标签之间的文本添加下划线。

- color

  颜色文本标签将自身及其闭合标签内的文本渲染为特定的颜色值。颜色值使用#rgb、#rgba、#rrggbb或#rrggbbaa格式。

- cps

  cps标签用于指定其闭合标签内的文本每秒钟显示的字符数，若带星号`*`，则表示当前速度的倍数。

  ```renpy
  label start:

    "{cps=30}时间要开始加速了！{/cps}"

    return
  ```

- font

  字体标签将标签自身及其闭合区间之间的文本渲染为指定的字体。入参即使用的字体文件名或路径。

- image

  图片标签会在文本中内插一个图片。内插的图片高度应该和单行文本的高度一致。入参可以是图片文件名，路径或者使用image语句定义的图像名。

- size

  字号标签改变了其自己及其闭合标签内的文本字号。若参数为整数则表示文本大小，若为一个星号`*`加一个浮点数的形式则表示为当前文本大小的倍数大小。

- fast

  fast标签只能用于对话中（即say语句），改标签为自闭和标签，在该标签前面的文本内容会立即显示。

  ```renpy
  label start:

    "你说"
    "什么？！{fast}"

    return
  ```

- nw

  nw标签同样只能用于对话中（即say语句），是一个自闭合标签，该标签前的那行文本内容在显示一次后会立刻消失，显示下一句话。

  ```renpy
  label start:

    "什么东西？{nw}"
    "？可恶"

    return
  ```

#### _函数

_函数表示其参数（应为一个字符串）是可被翻译的（如果有人翻译你的游戏）。

```renpy
define s = Character(name=_("Sylvie"))
```

#### 角色（Character）对象

>提示：这一部分面向对象概念内容属于拓展知识，可以选择跳过。
>
>对象（Object）是一个面向对象编程的概念，与之对应的类（class）。简单来说，对象就是一堆数据的封装，是类的实例化；而类就是具有相似属性和行为的总称，一个对象就是类的一个实例。Python跟很多高级语言（如Java）一样都是面向对象（object-oriented）编程。由于Ren'Py是基于Python的，所以Ren'Py中也存在类与对象，像ADVCharacter就是一个类。

我们一般使用Character函数（Character函数是一个构造器，用于构造并返回一个对象）定义一个角色对象。

```renpy
define s = Character(name=_("Sylvie"))
```

这样，我们就简单地定义了一个角色对象。

Character函数有很多个参数，常用的如下：

- name
  - 如果该参数是一个字符串，则成为对话中角色的名字。如果name参数是None，名字不会显示，用于旁白。

- kind
  - 新建角色的基底角色。该参数值通常为 *adv* 或 *nvl*。adv模式体现为文本显示在对话框中；而nvl模式体现为文本显示在屏幕中间。

- image
  - 与角色关联的图像标签名的字符串。
  
- who_color
  - 角色名的颜色，一般为一个表示颜色的十六进制数的字符串。

- what_color
  - 文本的颜色，一般为一个表示颜色的十六进制数的字符串。

- what_prefix
  - 显示对话内容之前，添加的前缀字符串。

- what_suffix
  - 显示对话内容之前，添加的后缀字符串。

- who_prefix
  - 显示角色名字之前，添加的前缀字符串。

- who_suffix
  - 显示角色名字之前，添加的后缀字符串。

- dynamic
  - 该参数若为True，角色名 name 应是一个包含python表达式的字符串。该字符串会在每行对话执行前先演算，将演算结果用作角色名。

- condition
  - 若给定，该参数应是一个包含python表达式的字符串。若表达式结果为False，对话不会发生，即say语句不会执行。

- ctc
  - 一个用做“点击继续”提示的可展现部件，若有其他特殊提示被使用时可能不会展现。

```renpy
define s = Character(
  name=_("Sylvie"),
  who_color="#FFA500",
  what_color="#FFE4E1",
  what_prefix="『",
  what_suffix="』",
)

label start:

  s "你好！"

  return
```

自己试试上面的代码有什么效果吧！

我们再来定义一个nvl角色：

```renpy
define n = Character(
  name=None,
  kind=nvl
)

label start:

  n """
  先帝创业未半而中道崩殂，今天下三分，益州疲弊，此诚危急存亡之秋也。
  
  然侍卫之臣不懈于内，忠志之士忘身于外者，盖追先帝之殊遇，欲报之于陛下也。
  
  诚宜开张圣听，以光先帝遗德，恢弘志士之气，不宜妄自菲薄，引喻失义，以塞忠谏之路也。
  """ 

  nvl clear

  return
```

由三引号引起来的文本，Ren’Py会根据内容中的空行自动分段。分段后的每一段内容，都会创建自身的say语句。同时，由于nvl角色默认共用一个界面，所以说完话后记得使用`nvl clear`清空nvl界面。

### 图像（image）

>[附官方简中文档同步章节](https://www.renpy.cn/doc/displaying_images.html#)

图像是视觉小说类游戏不可或缺的东西，在Ren'Py中图像是一类可以使用show语句显示在屏幕上的东西统称，可以是一个可视组件或一张图片等。而Ren'Py给我们提供了一些关于图像的语句。

它们分别是：

1. image语句。
2. show语句。
3. scene语句。
4. hide语句。

#### image语句

我们使用`image`关键字来定义一个图像。

```renpy
image bg night = "images/bg_night.jpg"
```

*bg night* 是图像名，而后面则是图片的路径。

一个图像名可能包含一个或多个字段，由空格分隔。图像名的第一个字段称作 *图像标签（tag）*。 后面的字段被称作 *图像属性（attribute）*。

*bg* 就是一个图像标签，*night* 是一个图像属性。

image语句还能把一个可视组件或一个表示颜色的十六进制数的字符串定义为图像：

```renpy
image bg night = "images/bg girl.jpg"
image black = "#000000"
image symbol = Text("Ren'Py")
```

除此之外，image语句还支持带有ATL语句块。详细在后面的ATL语句块部分再讲。

#### show语句
