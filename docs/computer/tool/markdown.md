# 搭建网页
## mkdocs工具介绍
markdwon语法的初衷是希望人们更专注于内容而非格式，Mkdocs也是如此。可以用Django，用Flask生成更精美的网页，但没有必要。因此，选择Mkdocs来负责把文档生成为网页，自己可以则专注于内容，而非排版，布局，调色等。官网：<https://www.mkdocs.org/getting-started/>
## 1. 在本地安装依赖的工具
- `pip install python`:如果已经安装了python，忽略
- `pip install mkdocs`: 安装Mkdocs
- `pip install mkdocs-material`: 下载安装material主题  
查看一下安装情况
- `python -V`
- `mkdocs`
## 2. 创建网页本地文件夹
- `cd ~/Desktop/`:进入到桌面文件夹
- `mkdocs new mysite`: 在桌面文件夹下创建`mysite`网页文件夹
## 3. 使用Github提供的Pages发布
- 来到Github网站，为网页创建仓库  
GitHub > Repository > New 
-  仓库的名称格式“`<自己的用户名>.github.io`”:（如果用户名称包含大写字母，必须改写为小写字母。）
- 单击 Create repository
- 设置仓库
    - GitHub > Repository > Settings > Actions > General >
        - Actions permissions: Allow all actions and reusable workflows
        - Workflow permissions: Read and write permissions
        - Click Save
## 4. 来到本地terminal
- 进入到桌面文件夹：`cd ~/Desktop/`
- 克隆仓库到本地：`git clone git@github.com:tian-jun/tian-jun.github.io.git`: 
- 将mysite文件夹下面的内容复制到tian-jun.github.io文件夹下
- 进入到克隆下来的仓库文件夹下：`cd ~/tian-jun.github.io/`
- 创建GitHub工作流文件夹和文件
  - `mkdir .github`
  - `cd .github`
  - `mkdir workflows`
  - `cd workflows`
  - `vim PublishMysite.yml`
    - 在PublishMysite.yml文件中输入以下内容
```
name: publishMysite
on: # 在什么时候触发工作流
  push: # 在从本地main分支被push到GitHub仓库时
    branches:
      - main
  pull_request: # 在main分支合并别人提的pr时
    branches:
      - main
jobs: # 工作流的具体内容
  deploy:
    runs-on: ubuntu-latest # 创建一个新的云端虚拟机 使用最新Ubuntu系统
    steps:
      - uses: actions/checkout@v2 # 先checkout到main分支
      - uses: actions/setup-python@v2 # 再安装Python3和相关环境
        with:
          python-version: 3.x
      - run: pip install mkdocs-material # 使用pip包管理工具安装mkdocs-material
      - run: mkdocs gh-deploy --force # 使用mkdocs-material部署gh-pages分支
```
## 5. 将更改的内容推送到`tian-jun.github.io`仓库
- 命名远程仓库的简写：`git remote add origin git@github.com:tian-jun.github.io.git`
- 重命名刚刚创建的分支：`git branch -m main`
- 把所有文件加入到暂存区：`git add .`
- 提交：`git commit -m "备注信息"`
- 推送到origin（tian-jun.github.io）仓库：`git push -u origin main`
- 设置网址发布的资源库 
GitHub > Repository > Settings > Pages > Source > gh-pages > Click Save
- 等待几分钟[查看网页](https://tian-jun.github.io/)
    - 网页地址就是仓库名称`https://tian-jun.github.io`
## 6. 其他发布方式
- 本地发布
  - 进入网页文件：`cd tian-jun.github.io`
  - 通过本地端口发布网站（仅可在本地浏览）：`mkdocs serve`
  - 编辑了文件，实时更新到网站上
  - 键盘按`control+C`退出
- 第三方服务器发布
  - 生成网页文件：`mkdocs build`
  - 输入上命令后,文件夹下会多出site文件夹，上传文件到`www.bitballoon.com`
## 7. 常见问题修复
- 异常信息：
`! [remote rejected] master -> master (push declined due to email privacy restrictions)`
- 异常原因：配置git时设置了作者邮箱信息，触发了Github 隐私保护设置：`Block command line pushes that expose my email`
- 解决方法：更改 git 配置的邮件地址
  - `git config --global user.email`查看当前的全局用户Email
  -  找到你 GitHub 给的推荐 Email
  - 在 settting --> Email --> keep my Email private 选项下的 Email；格式是：`id+username@users.noreply.github.com`
  - 重新设置你的全局用户 Email： `git config --global user.email "GitHub 给的推荐 Email"`
  - 重置上次提交的作者信息:`git commit --amend --reset-author`
  - 输入命令后，进入vi模式（ git 默认的编辑器）；在英文输入法下`:wq`(冒号wq)保存退出
  - 提交到github仓库，如果没有其他问题，大功告成:`git push origin main`



