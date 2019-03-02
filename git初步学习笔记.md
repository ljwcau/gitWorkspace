### Markdown插入图片的方法：https://blog.csdn.net/SlaughterDevil/article/details/79255933#插入本地图片
----

## 学习git实践
### 一、初始用户名与邮箱设置：
- hasee@DESKTOP-8HHLSJO MINGW64 ~
$ git config --global user.name "Luo"

- hasee@DESKTOP-8HHLSJO MINGW64 ~
$ git config --global user.email "838047310@qq.com"
---
### 二、基本命令
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
- git reset hard 版本号 回退到那个版本



