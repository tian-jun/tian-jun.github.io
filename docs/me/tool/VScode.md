# 用终端写代码

cd到目标文件夹

```plain
mkdir cpp
cd cpp
touch hello.cpp
vim hello.cpp
#按<i>进入插入模式，就可以开始写代码了
#按<ESC>退编辑模式，按冒号<：>，按<wq>退出
```

# 编译器 g++

将C++文件编译成计算机可以执行的二进制文件，使得电脑硬件可以直接执行。

安装g++

1. Xcode（软件太大了，不推荐）
2. 终端下载，输入一下代码，如果没有g++编译器，会提示你安装
3. [苹果开发者网站](https://developer.apple.com)（推荐）

```plain
g++ --version
```

用g++编译C++文件

```plain
which g++#查看环境变量
g++ hello.cpp#编译文件
./a.out#执行编译的文件
rm a.out#删除
g++ hello.cpp -o hello.out#给编译完的可执行文件取名字
g++ hello.cpp -o hello#不带后缀
```

# 终端写代码不爽的地方

* 没有代码高亮
* 没有错误提醒
* 没有易于阅读的格式

# VS Code

代码编辑器

优点

* 开源的，所有使用者都可以参与开发，版本迭代很快，功能齐全
* 轻量，262MB,对比Xcode 12个G
* 支持很多插件，可以用来编写所有的语言
* 个性化配置程度高，可以自己开发插件
  使用

command + k，command + T#修改主题

command + b#收起左侧边栏

control+~#打开终端 



