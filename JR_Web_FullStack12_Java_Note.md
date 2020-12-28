# 01 Introduction
# 02 HTML and CSS
# 03 CSS and SASS
# 04 JavaScript
# 05 Git

## 05 Git
A Distrbuted Version Control System.
尽量尝试使用command line来使用Git，但新手刚上手可以用Git GUI的一些软件来帮助做。(Github Desktop, SourceTree)
参考Git Cheat Sheet文件，把命令用熟
必须要包括Git Ignore，防止传入IDE建立project自带的文件
以主分支（以前是master, 现在是main）为基准

### 第一种方式建立repo （没有远端repo情况下）
git init：把你的project纳入版本控制
git clone：直接把repo抓下来（包括版本控制）
从课件Git Local Hands on开始多练习
···
mkdir learngit：创建learngit文件夹
cd learngit：进入learngit文件夹
pwd：显示当前路径
git init：版本控制初始化，将learngit文件夹纳入版本控制
touch README.md: 新建一个markdown文件（或者vi README.md或者用text editor的cli比如atom README.md)
git add README.md （将新文件添加到版本控制stage）
git status （查看当前repo文件是否commit）
git commit -m "组织合适的message" （可参考作业要求里面写的message）
git log （查看历史comment）
···
### 每次修改以后
···
git status （勤用这个命令查看当前repo的commit状态）
git add README.md （将新文件添加到版本控制）
git status （查看当前repo文件是否commit）
git commit -m "组织合适的message" （可参考作业要求里面写的message）
···
### git add相关
git add . （慎用，可以用git add . -p逐步查看并add）
必须要包括.gitignore，防止传入IDE建立project自带的文件
所有的password是绝对不能提交的
同时project相关configuration文件也不要交上去
所以上述文件需要放到.gitignore文件中
### Undo changes
git reset <comment> (到git log中找需要reset的commit，大部分情况使用reset)
git revert HEAD (如果之后还是需要访问旧的commit，使用revert)
使用https://git-school.github.io/visualizing-git/这个visualising的工具进行练习

git commit --amend (撤销之前的commit或者comment)
git stash （保存已做的修改，同时获取最新的代码版本）

### Teamworks
个人的branch不会有太多，公司工作需要在不同branches进行作业。
在teamwork下，需要有一个自己的branch，写好代码后生成pull request，Lead查看确认后可以把自己的branch merge到master上
git pull (从remote的repo把最新文件抓下来)
git checkout <branchname> （转换不同的branch）
git merge (将自己branch上的修改合并到master上，这之前必须solve所有的conflicts)
时刻更新主分支上的代码

### How to set personal token
https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/creating-a-personal-access-token

### Set up SSH key
https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent

Pull Request之前必须解决所有的conflicts
解决冲突，谁后提交谁解决冲突，一般在自己的代码上解决冲突，未经允许不要改别人的！！
如果遇到没有权限的repo，可以使用Fork加到自己的repo，做完修改之后可以apply a pull request against the original one
