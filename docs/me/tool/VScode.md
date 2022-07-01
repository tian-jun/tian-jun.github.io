# VS Code
### 用终端写代码
#### 使用vim编写代码
- `mkdir cpp`: 创建文件夹
- `cd cpp`: 进入到cpp文件夹
- `touch hello.cpp`: 创建hello.cpp文件
- `vim hello.cpp`: vim打开文件，按<i>进入插入模式，按<ESC>退编辑模式，英文输入法下，按冒号<: >，按<wq>退出

#### 编译器 g++
g++将C++文件编译成计算机可以执行的二进制文件，使得电脑硬件可以直接执行。
##### 安装g++
- Xcode（软件太大了，不推荐）
- `g++ --version`: 查看g++版本，如果没有g++编译器，会提示安装
  - [苹果开发者网站](https://developer.apple.com)（推荐）
##### 用g++编译C++文件
- `which g++`: 查看环境变量
- `g++ hello.cpp`: 编译文件
- `./a.out`: 执行编译的文件
- `rm a.out`: 删除
- `g++ hello.cpp -o hello.out`: 给编译完的可执行文件命名
- `g++ hello.cpp -o hello`: 不带后缀
#### 终端写代码缺点
- 没有代码高亮
-  没有错误提醒
-  没有易于阅读的格式
### VS Code代码编辑器
- 优点
  - 开源的，所有使用者都可以参与开发，版本迭代很快，功能齐全
  - 轻量，262MB,对比Xcode 12个G
  - 支持很多插件，可以用来编写所有的语言
  - 个性化配置程度高，可以自己开发插件
#### 快捷键
- 先按`command + k`后按`command + T`: 修改主题
- `command + b`: 收起左侧边栏
- `control + ~`: 打开终端 
- `control + option + N`: 编译执行代码

#### 代码运行自动化
- 安装插件Code Runner
- tasks.json
- launch.json




