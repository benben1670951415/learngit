Windows下使用git bush，用的是Linux命令，常用的几个文件操作命令如下：
括号内是Windows命令。
cd/e/xxx 切换到xxx目录(cd e:\xxx)
pwd  显示当前目录路径(cd)
ls  列出当前目录内容(dir)
touch xxx.txt  生成名为xxx.txt的空文件（copy null xxx.txt）
rm xxx.txt 删除xxx.txt文件（del xxx.txt）
mkdir xxx 建立xxx目录（md xxx）
rm -r xxx 删除目录（rd /s xxx）

cd ..表示退回到上个目录

1，设置用户名和邮箱：
$git config --global user.name "your name"
$git config --global user.email "00000@qq.com"

2，选择合适的位置，创建一个空目录：
$ cd /f/learngit 这是选择f盘的learngit目录：
$ mkdir example  在当前目录创建一个仓库。
$cd xxx意思是进入xxx目录。
$ cd example
$ pwd

3，通过git init命令把这个目录变成git可以管理的仓库：
$ git init

4，通过git add把文件添加到仓库：
$ git add readme.txt

5，通过git commit告诉git，把文件提交到仓库：
$ git commit -m"
-m后面的内容是对此次提交的说明"

6，通过git status命令查看当前结果，掌握仓库当前的状态：
$ git status

7，通过git diff readme.txt查看具体修改情况：
$ git diff readme.txt
通过git log命令查看修改记录，也就是你曾经提交过的版本情况：
$ git log

8，简略显示版本信息：
$ git lot --pretty=oneline

9，版本回退：
git中head表示当前版本，HEAD^,HEAD^^,分别表示上一个，上上一个，也可以用HEAD~100，第100个之前的版本。
git reset --hard HEAD^是回退到上一个版本。
git reflog是查看命令历史,通过它可以回到“未来”，只要你能够找到未来的版本号。
$ git reflog

10，工作区和暂存区：
工作区就是电脑里能看到的目录，暂存区是git版本库里面的一个部分，它存放我们add了但是还没有提交到当前分支的内容。
git commit就是把暂存区里面的东西提交到分支，我们可以add多次，然后一次提交。

11，管理修改：每次提交的是修改，所做的修改必须先添加到暂存区，然后才能提交到分支，如果不添加到暂存区，则不会提交。

12，撤销修改：
修改了本地文件，未添加到暂存区的修改的撤销：
$ git checkout --learngit.txt意思就是说，用版本库里的最新内容替换本地文件。
add了即添加到暂存区，但是还未提交的修改的撤销：
git reset HEAD file可以把暂存区的修改撤销掉。
提交了的文件修改的撤销：参考版本回退

13，删除文件：
本地删除：$ rm test.txt
误删恢复：$ git checkout --test.txt
从版本库里删除：
git rm test.txt并且提交。

14，远程仓库：
创建自己的ssh key：$ ssh-keygen -t rsa -C "youremail@example.com"
这样之后，主目录里面会有一个.ssh目录：
id_rsa:这个是私匙，不能泄露
id_rsa.pub：这个是公匙。可放心的告诉任何人。
然后登陆自己的github添加ssh key；命名后，将id_rsa.pub添入。

15，添加远程库：
西安创建远程库，然后在本地相应库的目录下运行：
$ git remote add origin git@github.com:你的账户名/远程仓库名.git 
此时，远程库的名字叫origin。
推送本地内容到远程仓库：
$ git push -u origin master
由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，
还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。



