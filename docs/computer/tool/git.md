
# [Git](https://git-scm.com/book/zh/v2)

Git数据库中保存的信息都是以文件内容的哈希值来索引，而不是文件名。

### 三种状态
- modified,表示修改了文件，但是还没有保存到数据库中
- staged,表示对一个已修改文件的当前版本做了标记，使之包含在下次提交的快照中
- committed,表示数据已经安全地保存在本地数据库中
### 工作区，暂存区以及git仓库
- 工作区是对项目的某个版本独立提取出来的内容。这些从Git仓库的压缩数据库中提取出来的文件，放在磁盘上供你使用或修改。
- 暂存区是一个文件，保存了下次将要提交的文件列表信息一般在 Git 仓库目录中。 按照 Git 的术语叫做“索引”，不过一般说法还是叫“暂存区”。
- Git 仓库目录是 Git 用来保存项目的元数据和对象数据库的地方。 这是 Git 中最重要的部分，从其它计算机克隆仓库时，复制的就是这里的数据。
#### 基本的 Git 工作流程如下：
1. 在工作区中修改文件。
2. 将你想要下次提交的更改选择性地暂存，这样只会将更改的部分添加到暂存区。
3. 提交更新，找到暂存区的文件，将快照永久性存储到 Git 目录。
如果Git目录中保存着特定版本的文件，就属于committed状态。如果文件已修改并放入暂存区，就属于staged状态。如果自上次检出后，作了修改但还没有放到暂存区域，就是modified状态。
-hard 5d83f9e）

### 安装git
- `git --version`查看git版本
### Git配置
#### git config: 是一个高度可定制的工具
- `git config --global user.name "Jun"`设置用户名，每一个 Git 提交都会使用，会写入到每一次提交中，不可更改
- `git config --global user.email juntian.job@gmail.com`设置邮件地址，每一个Git提交都会使用，会写入到每一次提交中，不可更改
- `git config --global core.editor vim`配置默认文本编辑器
- `git config --list`查看配置，还可以加入`--show-origin`查看配置所在的文件位置
### Git 的基础命令行接口
- 获取 git 命令的帮助信息
    - `git help <command>`or`git <command> --help`or`man git<command>`
    - `git <command> -h`简明的help输出
- 创建一个新的git仓库
    - `git init`: 创建一个新的 git 仓库，其数据会存放在一个名为 .git 的目录下
        - `.git`:文件如果被隐藏了，命令行输入`defaults write com.apple.finderAppleShowAllFiles TRUE `,然后再在命令行输入`killall Finder`重启Finder应用
- 从服务器上克隆已有的Git项目
    - `git clone --depth=1`: 浅克隆（shallow clone），不包括完整的版本历史信息
    - `git clone https://github.com/libgit2/libgit2`克隆一个Git仓库
    - `git clone https://github.com/libgit2/libgit2 mylibgit`自定义本地仓库名字
- 显示当前的仓库状态
    - `git status`: 
    - `git status -s`or`git status --short`: 间洁版
- 跟踪文件
    - `git add <filename>`: 添加文件到暂存区，开始跟踪该文件，进行版本管理
    - `git add <folder>`:参数是目录的路径，该命令将递归地跟踪该目录下的所有文件。
    - `git add .`:会监控工作区的状态树，使用它会把工作时的所有变化提交到暂存区，包括文件内容修改(modified)以及新文件(new)，但不包括被删除的文件。
    - `git add -u`:仅监控已经被add的文件（即tracked file），会将被修改的文件提交到暂存区。add -u 不会提交新文件（untracked file）.（git add –update的缩写）
- 创建一个新的提交
    - `git commit`: 提交暂存区所有文件
    - `git commit -m "init"`: 
    - `git commit -a -m 'added new benchmarks'`: 已经跟踪的文件，被修改了，跳过暂存区,直接提交到分支上,不会提交新建的还没有跟踪的文件
- 查看提交记录
    - `git log`:,会列出SHA-1效验和，提交作者和邮箱，提交时间，提交说明
    - `git log --all --graph --decorate`: 可视化历史记录（有向无环图）
    - `git log -p -2`，`-p`:额外显示每次提交所引出的差异，按补丁的格式输出，`-2`选项来限制显示最近的两次提交
    - `git log --stat`:额外显示每次提交的简略统计信息
    - `git log --pretty=oneline`: `--pretty`可以使用不同于默认格式的方式展示提交历史，`oneline`会将每个提交放在一行显示
    - `git log --pretty=format:"%h - %an, %ar : %s`:定制显示格式
    - `git log --pretty=format:"%h %s" --graph`: oneline 或 format 与另一个 log 选项 --graph 结合使用时尤其有用
- 对比不同区域文件的差异
    - `git diff <filename>`: 比较工作区当前文件和与暂存区文件的差异，也就是修改之后还没有暂存起来的变化内容
    - `git diff --staged`: 比对已暂存文件与最后一次提交的文件差异
    - `git diff <revision> <filename>`: 显示某个文件两个版本之间的差异  
- 分支和合并
    - `git branch <name>`: 创建分支
    - `git branch -f <分支> HEAD~3`,`-f`将分支强制指向HEAD的第三级父节点  
    - `git branch -m <name>`重命名刚创建的分支
    - `git checkout -b <name>`: 创建分支并切换到该分支,相当于 `git branch <name>; git checkout <name>`
    - `git checkout main^`将HEAD移动到main的父节点上
    - `git checkout HEAD~4`将HEAD向父节点移动4次，
    - `git checkout <哈希值>`将HEAD移动到指定「提交记录」，Git 对哈希的处理很智能，你只需要提供能够唯一标识提交记录的前几个字符即可。
    - `git checkout <revision>`: 更新 HEAD 和目前的分支
    - `git merge <revision>`: 合并到当前分支
    - `git branch`: 显示分支
    - `git cherry-pick C2 C4`:抓取C2和C4分支的提交到main上
    - `git rebase`: 将一系列补丁变基（rebase）为新的基线(main)
        - `git rebase -i HEAD~4`:调整HEAD后4个父节点的顺序，或者删除，然后合并到main上
- 远端操作
    - `git clone`: 从远端下载仓库,自动将其添加为远程仓库并默认以 “origin” 为简写
    - `git remote`: 列出远端服务器的简写
    - `git remote -v`:列出远端服务器的简写和对应的URL 
    - `git remote add <name> <url>`: 添加一个远端
    - `git remote show origin`: 查看origin远程仓库 
    - `git remote rename <before> <new>`: 重命名远程仓库，值得注意的是这同样也会修改你所有远程跟踪的分支名字
    - `git remote remove <name>`: 移除远程仓库，一旦使用这种方式删除了一个远程仓库，所有和这个远程仓库相关的远程跟踪分支以及配置信息也会一起被删除
    - `git branch --set-upstream-to=<remote>/<remote branch>`: 创建本地和远端分支的关联关系
    - `git fetch`: 这个命令会访问远程仓库，从中拉取所有本地还没有的数据。执行完成后，本地将会拥有那个远程仓库中所有分支的引用，可以随时合并或查看。
    - `git fetch origin`:会抓取克隆（或上一次抓取）后新推送的所有工作。必须注意`git fetch`命令，只会将数据下载到你的本地仓库——它并不会自动合并或修改你当前的工作。当准备好时你必须手动将其合并入你的工作。
    - `git merge`: 合并分支
    - `git pull`: 相当于 git fetch; git merge
    - `git push <remote> <local branch>:<remote branch>`: 将对象传送至远端并更新远端引用
    - `git push origin main`等价于`git push origin main:main`: 只有当你有所克隆服务器的写入权限，并且之前没有人推送过时，这条命令才能生效
    - `git push -u origin main`: 
- 撤销
    - `git commit --amend`: 编辑提交的内容或信息
    - `git reset HEAD <file>`: 恢复暂存的文件
    - `git reset HEAD~1`
    - `git revert HEAD`:`C2`后面多了一个新提交！这是因为新提交记录`C2'`引入了更改,这些更改刚好是用来撤销C2这个提交的。也就是说`C2'`的状态与`C1`是相同的。revert之后就可以把你的更改推送到远程仓库与别人分享啦。   
    - `git restore`: git2.32版本后取代git reset 进行许多撤销操作
- 移出文件
    - `git rm <filename>`移出文件，下一次提交时，该文件就不再纳入版本管理了。 如果要删除之前修改过或已经放到暂存区的文件，则必须使用强制删除选项 -f。
    - `git rm --cached <filename>`,移除git跟踪，但保留在工作区
    - `git rm log/\*.log`, 删除 log/ 目录下扩展名为 .log 的所有文件
- 重命名文件
    - `git mv <file_from> <file_to>`, 把文件名`<file_from>`改为`<file_to>`，相当于下面三条命令  
        - `mv README.md README`
        - `git rm README.md`
        - `git add README`
- `.gitignore`文件
一般我们总会有些文件无需纳入 Git 的管理，也不希望它们总出现在未跟踪文件列表。 通常都是些自动生成的文件，比如日志文件，或者编译过程中创建的临时文件等。 在这种情况下，我们可以创建一个名为 .gitignore 的文件，列出要忽略的文件的模式。 来看一个实际的 .gitignore 例子：
```
$ cat .gitignore
*.[oa]
*~
```
第一行告诉 Git 忽略所有以 .o 或 .a 结尾的文件。一般这类对象文件和存档文件都是编译过程中出现的。  
第二行告诉 Git 忽略所有名字以波浪符（~）结尾的文件，许多文本编辑软件（比如 Emacs）都用这样的文件名保存副本。 此外，你可能还需要忽略 log，tmp 或者 pid 目录，以及自动生成的文档等等。 要养成一开始就为你的新仓库设置好 .gitignore 文件的习惯，以免将来误提交这类无用的文件。  
- .gitignore 的格式规范如下：
    - 所有空行或者以 # 开头的行都会被 Git 忽略。
    - 可以使用标准的 glob 模式匹配，它会递归地应用在整个工作区中。
    - 匹配模式可以以（/）开头防止递归。
    - 匹配模式可以以（/）结尾指定目录。
    - 要忽略指定模式以外的文件或目录，可以在模式前加上叹号（!）取反。
所谓的glob模式是指shell所使用的简化了的正则表达式。星号（*)匹配零个或多个任意字符；
[abc]匹配任何一个列在方括号中的字符（这个例子要么匹配一个a，要么匹配一个b，要么匹配一个c）；
问号（?）只匹配一个任意字符；
如果在方括号中使用短划线分隔两个字符，表示所有在这两个字符范围内的都可以匹配（比如 [0-9] 表示匹配所有 0 到 9 的数字）。使用两个星号`**`表示匹配任意中间目录，比如 `a/**/z` 可以匹配 `a/z` 、 `a/b/z`或 `a/b/c/z`等。我们再看一个 .gitignore 文件的例子：  
```
# 忽略所有的 .a 文件
*.a
# 仍跟踪所有的 lib.a，即便你在前面忽略了 .a 文件
!lib.a
# 只忽略当前目录下的 TODO 文件，而不忽略 subdir/TODO
/TODO
# 忽略任何目录下名为 build 的文件夹
build/
# 忽略 doc/notes.txt，但不忽略 doc/server/arch.txt
doc/*.txt
# 忽略 doc/ 目录及其所有子目录下的 .pdf 文件
doc/**/*.pdf
```
### 资源
- [Pro Git](https://git-scm.com/book/en/v2)，强烈推荐！学习前五章的内容可以教会您流畅使用Git的绝大多数技巧，因为您已经理解了Git的数据模型。后面的章节提供了很多有趣的高级主题。（Pro Git 中文版）；
- [Oh Shit, Git!?!](https://ohshitgit.com/) ，简短的介绍了如何从 Git 错误中恢复；
- [Git for Computer Scientists](https://eagain.net/articles/git-for-computer-scientists/) ，简短的介绍了 Git 的数据模型，与本文相比包含较少量的伪代码以及大量的精美图片；
- [Git from the Bottom Up](https://jwiegley.github.io/git-from-the-bottom-up/)详细的介绍了Git的实现细节，而不仅仅局限于数据模型。好奇的同学可以看看；
- [How to explain git in simple words](https://xosh.org/explain-git-in-simple-words/)；
- [Learn Git Branching](https://learngitbranching.js.org/?locale=zh_CN)通过基于浏览器的游戏来学习Git；

