### Markdown插入图片的方法：https://blog.csdn.net/SlaughterDevil/article/details/79255933#插入本地图片
----
# 学习git实践
## 一、初始用户名与邮箱设置：
- hasee@DESKTOP-8HHLSJO MINGW64 ~
$ git config --global user.name "Luo"
- hasee@DESKTOP-8HHLSJO MINGW64 ~
$ git config --global user.email "xxxxx@qq.com"
---
## 二、基本命令
- cd S:进入目录
- mkdir gitWorkspace 创建git目录
- pwd 显示当前目录
- git init 把这个目录变成git可以管理的仓库
- git add readme.txt、git commit -m “后面加注释" 将文件readme.txt提交到仓库
- git status 查看状态
- 修改后的文件再提交，也是add、commit的步骤
- git diff readme.txt 查看修改了哪些内容
- git log 查看历史记录
- git log --pretty=oneline 一行查看历史记录
- git reset --hard HEAD^ 回退到上一个版本
- git reset  --hard HEAD~100 回退到前100个版本
- cat readme.txt 在命令行查看readme.txt的内容
- git reflog 查看历史记录版本号
- git reset --hard 版本号 回退到那个版本
## 三、理解工作区与暂存区
    工作区：就是你在电脑上看到的目录，比如目录下testgit里的文件(.git隐藏目录版本库除外)。或者以后需要再新建的目录文件等等都属于工作区范畴。
    版本库(Repository)：工作区有一个隐藏目录.git,这个不属于工作区，这是版本库。其中版本库里面存了很多东西，其中最重要的就是stage(暂存区)，还有Git为我们自动创建了第一个分支master,以及指向master的一个指针HEAD。
我们前面说过使用Git提交文件到版本库有两步：
- 第一步：是使用 git add 把文件添加进去，实际上就是把文件添加到暂存区。
- 第二步：使用git commit提交更改，实际上就是把暂存区的所有内容提交到当前分支上。
---
## 四、撤销修改
命令 git checkout --readme.txt 意思就是，把readme.txt文件在工作区做的修改全部撤销，这里有2种情况，如下：
- readme.txt自动修改后，还没有放到暂存区，使用 撤销修改就回到和版本库一模一样的状态。
- 另外一种是readme.txt已经放入暂存区了，接着又作了修改，撤销修改就回到添加暂存区后的状态。
### 删除文件
- rm b.txt 在文件目录删除b.txt
再执行git rm 文件名、git commit -m “ ”，在仓库中删除
- git checkout  -- b.txt 若在没有commit之前，可以用checkout恢复文件
---
## 五、远程仓库
### 1、需要ssh key来与github相连
如何生成SSH key - 简书  https://www.jianshu.com/p/31cbbbc5f9fa/
- 本机操作：输入ssh-keygen -t rsa -C "your_email@example.com"后只按了回车
### 2、登录github
打开” settings”中的SSH Keys页面，然后点击“Add SSH Key”,填上任意title，在Key文本框里黏贴id_rsa.pub文件的内容。
### 3、使github上的仓库与本地仓库同步
- 1、登录github上，然后在右上角找到“create a new repo”创建一个新的仓库
- 2、把一个已有的本地仓库与之关联，然后，把本地仓库的内容推送到GitHub仓库- 
- 3、在本地bash中运行：
    - （1）git remote add origin https://github.com/ljwcau/gitWorkspace.git
    - （2） git push -u origin master

由于远程库是空的，我们第一次推送master分支时，加上了 –u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来

    从现在起，只要本地作了提交，就可以通过如下命令：git push origin master，把本地master分支的最新修改推送到github上了，现在你就拥有了真正的分布式版本库了

### 4、克隆远程仓库
用git clone克隆将一个远程仓库克隆岛本地
### 5、创建与合并分支
    每次提交，Git都把它们串成一条时间线，这条时间线就是一个分支。截止到目前，只有一条时间线，在Git里，这个分支叫主分支，即master分支。HEAD严格来说不是指向提交，而是指向master，master才是指向提交的，所以，HEAD指向的就是当前分支。

- git checkout -b dev 创建并切换到dev新的分支山（与git branch dev、git checkout dev两条命令作用相同）
    - git branch查看分支，会列出所有的分支，当前分支前面会添加一个星号。
    - git checkout xx查看xx分支

- 在master分支上，使用如下命令 git merge dev 将dev分支上的内容合并到分支master上，随后可以用git branch –d dev删除dev分支。
----
    总结创建与合并分支命令如下：
- 查看分支：git branch
- 创建分支：git branch name
- 切换分支：git checkout name
- 创建+切换分支：git checkout –b name
- 合并某分支到当前分支：git merge name
- 删除分支：git branch –d name

        通常合并分支时，git一般使用”Fast forward”模式，在这种模式下，删除分支后，会丢掉分支信息，现在我们来使用带参数 –no-ff来禁用”Fast forward”模式。合并dev分支，使用命令 git merge –no-ff  -m “注释” dev

分支策略：首先master主分支应该是非常稳定的，也就是用来发布新版本，一般情况下不允许在上面干活，干活一般情况下在新建的dev分支上干活，干完后，比如上要发布，或者说dev分支代码稳定后可以合并到主分支master上来。

    20190302 17:11
    参考：Git使用教程,最详细，最傻瓜，最浅显，真正手把手教_慕课手记  http://www.imooc.com/article/20411





