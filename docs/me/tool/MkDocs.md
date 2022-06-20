# 构建自己的网站

## [我的网页](https://tian-jun.github.io)
- https://tian-jun.github.io
## [mkdocs工具介绍](https://www.mkdocs.org/getting-started/)
markdwon语法的初衷是希望人们更专注于内容而非格式，Mkdocs也是如此。可以用Django，用Flask生成更精美的网页，但没有必要。因此，选择Mkdocs来负责把文档生成为网页，自己可以则专注于内容，而非排版，布局，调色…
## 安装需要的工具
- `pip install python`:如果已经安装了python，忽略
- `pip install mkdocs`: 安装Mkdocs
- `pip install mkdocs-material`: 下载安装material主题
## 查看安装情况
- `python -V`
- `mkdocs`
## 创建网页
- `cd ~/Desktop/`:进入到桌面文件夹
- `mkdocs new mysite`: 在桌面文件夹下创建`mysite`项目文件
## 使用Github Pages发布
- 为网站创建仓库
1. GitHub > New Repository 
2. `<user>.github.io`:仓库的名称格式（用户名称包含大写字母，必须改写为小写字母。）
3. 单击 Create repository
- 设置仓库
    - GitHub > Repository > Settings > Actions > General >
        - Actions permissions: Allow all actions and reusable workflows
        - Workflow permissions: Read and write permissions
        - Click Save
- `git clone git@github.com:tian-jun/tian-jun.github.io.git`: 克隆仓库到本地
- 将mysite文件夹下面的内容复制到tian-jun.github.io文件夹下
- 创建GitHub工作流
```
mkdir .github
cd .github
mkdir workflows
cd workflows
vim PublishMysite.yml
```
- 键入PublishMysite.yml文件以下内容
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
- 将更改的内容推送到`tian-jun.github.io`仓库
    - `git remote add origin git@github.com:tian-jun.github.io.git`: 命名远程仓库的简写
    - `git branch -m main`: 重命名刚刚创建的分支
    - `git add .`: 把所有文件加入到暂存区
    - `git commit`: 提交
    - `git push -u origin main`:推送到origin（tian-jun.github.io）仓库
- 等待几分钟[查看网页](https://tian-jun.github.io/)
    - `tian-jun.github.io`:网页地址
## 其他发布方式
- `cd mysite`:进入网页文件
- `mkdocs serve`:通过本地端口发布网站（仅可在本地浏览），编辑了文件，实时更新到网站上，键盘输入`control+C`退出
- `mkdocs build`:输入该命令后,mysite文件夹下会多出site文件夹，上传文件到`www.bitballoon.com`
### 问题修复
- 异常信息：
`! [remote rejected] master -> master (push declined due to email privacy restrictions)`
- 异常原因：配置git时设置了作者邮箱信息，触发了Github 隐私保护设置：`Block command line pushes that expose my email`
- 解决方法：更改 git 配置的邮件地址
1. `git config --global user.email`查看当前的全局用户Email
2. 找到你 GitHub 给的推荐 Email
在 settting --> Email --> keep my Email private 选项下的 Email；格式是：`id+username@users.noreply.github.com`
3. 重新设置你的全局用户 Email： git config --global user.email "GitHub 给的推荐 Email"
4. `git commit --amend --reset-author`:重置上次提交的作者信息 
输入命令后，进入vi模式（ git 默认的编辑器）；在英文输入法下`:wq`(冒号wq)保存退出
5. `git push origin main`提交到github仓库，如果没有其他问题，大功告成。

## 显示图片
- `cd docs`:进入docs文件夹
- `midir img`:创建img文件夹，把需要加载的文件放在该文件夹下面，然后在文件中输入`![](/img/<文件名.后缀>)`，即可显示该图片。

## 显示数学公式
- 使用[mathjax](https://mathjax-chinese-doc.readthedocs.io/en/latest/#)工具
- 在需要编写数学公式的文件末尾粘贴如下代码
```
<script type="text/javascript" async
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.7/MathJax.js?config=TeX-MML-AM_CHTML">
</script>
<script type="text/x-mathjax-config">
MathJax.Hub.Config({
  tex2jax: {inlineMath: [['$','$'], ['\\(','\\)']]}
});
</script>
```
- 平方
    - 代码
`$a^2 + b^2 = c^2$`: 如果左右两边是两个`$$`，则居中对齐
- 效果
$a^2 + b^2 = c^2$
- 根号
    - 代码：`$\sqrt{2}$`，
    - 效果 $\sqrt{2}$
- 更多的数学编写方式Google搜索mathjax symbols 


<script type="text/javascript" async
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.7/MathJax.js?config=TeX-MML-AM_CHTML">
</script>
<script type="text/x-mathjax-config">
MathJax.Hub.Config({
  tex2jax: {inlineMath: [['$','$'], ['\\(','\\)']]}
});
</script>

