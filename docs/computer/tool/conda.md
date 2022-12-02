# 常用工具

### 进入conda官网下载合适的版本
https://docs.conda.io/en/latest/miniconda.html
### 安装
	bash /Users/tianjun/Downloads/Miniconda3-py38_4.10.1-MacOSX-arm64.sh
### 初始化shell,其实就是将conda路径写入shell配置
	conda init zsh
	conda init
### 创建虚拟环境
	conda create -n myspaceone python=3.8 pip
### 激活虚拟环境 
	conda activate myspaceone
### 查看python版本和python路径
	python -V
注意：V需要大写
	which python
### 查看conda有哪些虚拟环境
	conda env list
### 安装依赖环境
	pip install -y jupyter notebook


### 显示当前路径
	pwd
### 切换路径
	cd ..#返回上一级目录
	cd ~#返回根目录

### 创建文件夹
	mkdir <文件夹名>
### 创建C++文件
	touch <文件名.cpp>
### 指定应用打开文件
	open <文件名.cpp> -a textedit.app
### g++编译
	g++  <文件名.cpp> -o hello.out


### 命令行打开可执行文件
	./a.out
	/Users/tianjun/Desktop/math/a.out
### 删除文件
	rm <文件名.cpp>






