# 个人网站构建 
## mkdocs工具介绍
markdwon语法的初衷是希望人们更专注于内容而非格式， Mkdocs也是如此。 你可以用Django， 用Flask 生成更精美的网页，但没有必要。因此，Mkdocs来负责把文档生成为网页，你则专注于内容， 而非排版，布局， 调色…
## 安装环境
    pip install python
    pip install mkdocs
## 查看安装情况
    python -V
    mkdocs
## 创建网站文件
    cd ~/Desktop/
    mkdocs new mysite
## 运行网站 
    cd mysite/
    mkdocs serve
    control+C 退出
## 显示图片
在docs文件夹下创建img文件夹，把需要加载的文件放在该文件夹下面
    ![](/img/<文件名.后缀>)
## 显示数学公式
Google搜索mathjax，在需要编写数学公式的文件末尾加入两段代码
更多的数学编写方式Google搜索mathjax symbols 

$$
a^2 + b^2 = c^2
$$
$\sqrt{2}$

## 网站结构
编辑mkdocs.yml文件
## 网站主题
 Google搜索mkdocs themes material下载安装
    pip install mkdocs-material
## 发布网站
    mkdocs build
mysite文件夹下会多出site文件夹，压缩该文件夹为zip格式
上传压缩文件到www.bitballoon.com

<script type="text/javascript" async
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.7/MathJax.js?config=TeX-MML-AM_CHTML">
</script>
<script type="text/x-mathjax-config">
MathJax.Hub.Config({
  tex2jax: {inlineMath: [['$','$'], ['\\(','\\)']]}
});
</script>

