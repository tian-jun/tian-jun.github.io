# [MarkDown](https://markdown.com.cn/basic-syntax/)

## 图床
### github + PicGo解决方案
- 下载PicGo：`brew install picgo --cask`
    - 下载安装brew：`/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"` （如果不显示`command not found: brew`,忽略）
    - PicGo打不开的解决方法：<https://support.apple.com/zh-cn/HT202491>: 
- 配置图床
    - 在GitHub上创建存储图片的仓库
    - 生成token
    - 在PicGo里填写相应信息，点击保存即可。
    - 将需要加入到MarkDown文件中的图片拖拽到PicGo，即可生成该图片的超链接
## 文字
- `~~删除线~~`这就是 ~~删除线~~ (使用波浪号)
- `*斜体* ` *斜体* 
- `**加粗** `**加粗**
- `***斜体+加粗***`***斜体+加粗***
- 高亮（需勾选扩展语法）
- 下标`水 H~2~O,双氧水 H~2~O~2~`水 H~2~O 双氧水 H~2~O~2~
- 上标（需勾选扩展语法）`面积 m^2^,体积 m^3^`面积 m^2^,体积 m^3^
## 代码
- 一个点`，行间代码块
- 三个点`，多行代码块
## 列表
- 无序列表`- `
- 有序列表`1. `
## 段落
- 换行
    - 行末加两个空格
    - HTML的`<br>`标签
- `<u>下划线</u>`<u>下划线是HTML语法</u>
- 居中：`<center>月是故乡明</center>`,Markdown语法本身没有居中，但支持HTMl语法
- 左对齐：`<p align="left">月是故乡明</p>`
- 右对齐：`<p align="right">月是故乡明</p>`

## 表格
- 使用 `|` 来分隔不同的单元格，使用 `-` 来分隔表头和其他行
- 为了美观，`|` 和 `-` 两侧需要至少有一个空格（最左侧和最右侧的 `|` 外就不需要了）
| name          | price |
| ------------- | ----- |
| fried chicken | 19    |
| cola          | 5     |

## 表情符号
Emoji 支持表情符号，你可以用系统默认的 Emoji 符号（ Windows 用户不一定支持）。也可以用图片的表情，输入 `:` 将会出现智能提示。  (  Mac: `control`+`command`+`space`点选)

### 转换规则

代码块中的文本（包括 Markdown 语法）都会显示为原始内容


## 跳转
- `[link text](link)`:外部跳转--超链接
- `[link text](#要去的目的地--标题）`:内部跳转--本文件内跳（Typora支持）
- `<>`包括的URL或邮箱地址会被自动转换为超链接:自动链接

## 图片
- `![自己起的图片名字](图片地址或者图片本地存储的路径)`
- `<img src="" width="500" height="913" align="bottom" /> `:格式化图片
- `https://squoosh.app/`:图片压缩，Google开源免费

## 标题
```
井号的个数代表标题的级数
# 一级标题使用1个
## 二级标题使用2个
### 三级标题使用3个
#### 四级标题使4用个
##### 五级标题使用5个
###### 六级标题使用6个
最多支持六级标题
```
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
## 更多的数学编写方式Google搜索mathjax symbols 


<script type="text/javascript" async
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.7/MathJax.js?config=TeX-MML-AM_CHTML">
</script>
<script type="text/x-mathjax-config">
MathJax.Hub.Config({
  tex2jax: {inlineMath: [['$','$'], ['\\(','\\)']]}
});
</script>

