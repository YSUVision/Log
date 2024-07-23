# git笔记整理：

#### **git理解**

- 工作区：仓库的目录。工作区是独立于各个分支的。
- 暂存区：数据暂时存放的区域，类似于工作区写入版本库前的缓存区。暂存区是独立于各个分支的。
- 版本库：存放所有已经提交到本地仓库的代码版本
- 版本结构：树结构，树中每个节点代表一个代码版本。

#### .git里的文件

1. **objects**: 用于存储所有提交的快照(commit)、树(tree)以及 blob 对象。
2. **refs**: 存储指向 commit 对象的命名引用,如分支、标签等。
3. **HEAD**: 指向当前检出分支的引用。
4. **index**: 存储暂存区(staging area)的信息。
5. **config**: 存储当前仓库的配置信息。
6. **description**: 仓库的描述信息。
7. **hooks**: 存放自定义 Git 钩子脚本。
8. **info**: 存放一些全局性排除文件的规则。
9. **logs**: 存放各分支的更新日志。

#### **git命令**

1、git config --global user.name xxx：设置全局用户名，信息记录在~/.gitconfig文件中

2、git config --global user.email xxx@xxx.com：设置全局邮箱地址，信息记录在~/.gitconfig文件中

3、git init：将当前目录配置成git仓库，信息记录在隐藏的.git文件夹中

4、git add XX：将XX文件添加到暂存区

5、git add .：将所有待加入暂存区的文件加入暂存区

6、git rm --cached XX：将文件从仓库索引目录中删掉

7、git commit -m "给自己看的备注信息"：将暂存区的内容提交到当前分支

8、git status：查看仓库状态

9、git diff XX：查看XX文件相对于暂存区修改了哪些内容

10、git log：查看当前分支的所有版本

11、git reflog：查看HEAD指针的移动历史（包括被回滚的版本）

12、git reset --hard HEAD^ 或 git reset --hard HEAD~：将代码库回滚到上一个版本

13、git reset --hard HEAD^^：往上回滚两次，以此类推

14、git reset --hard HEAD~100：往上回滚100个版本

15、git reset --hard 版本号：回滚到某一特定版本

16、git checkout — XX或git restore XX：将XX文件尚未加入暂存区的修改全部撤销

17、git remote add origin 

18、git@git.acwing.com:xxx/XXX.git：将本地仓库关联到远程仓库

19、git push -u (第一次需要-u以后不需要)：将当前分支推送到远程仓库

20、git push origin branch_name：将本地的某个分支推送到远程仓库

21、git clone git@git.acwing.com:xxx/XXX.git：将远程仓库XXX下载到当前目录下

22、git checkout -b branch_name：创建并切换到branch_name这个分支

23、git branch：查看所有分支和当前所处分支

24、git checkout branch_name：切换到branch_name这个分支

25、git merge branch_name：将分支branch_name合并到当前分支上

26、git branch -d branch_name：删除本地仓库的branch_name分支

27、git branch branch_name：创建新分支

28、git push --set-upstream origin branch_name：设置本地的branch_name分支对应远程仓库的branch_name分支

29、git push -d origin branch_name：删除远程仓库的branch_name分支

30、git pull：将远程仓库的当前分支与本地仓库的当前分支合并

31、git pull origin branch_name：将远程仓库的branch_name分支与本地仓库的当前分支合并

32、git branch --set-upstream-to=origin/branch_name1 branch_name2：将远程的branch_name1分支与本地的branch_name2分支对应

git checkout -t origin/branch_name 将远程的branch_name分支拉取到本地

33、git stash：将工作区和暂存区中尚未提交的修改存入栈中

34、git stash apply：将栈顶存储的修改恢复到当前分支，但不删除栈顶元素

35、git stash drop：删除栈顶存储的修改

36、git stash pop：将栈顶存储的修改恢复到当前分支，同时删除栈顶元素

37、git stash list：查看栈中所有元素



#### git基本理解加部分操作步骤

1、git是通过树结构去维护历史版本的。

2、git config --global user.name jyt(随便起）

git config --global user.email git仓库的邮箱

3、git rm --cached XX：将文件从仓库索引目录中删掉//（暂存区中去掉的方法，去掉对文件的管理权）

git restore --staged 文件，将文件从暂存区去掉，仍拥有管理权。

**##git restore --staged 文件（暂存区->工作区），git restore 文件（回退到上个节点）##**

4、git restore 文件  此操作是操作在工作区的文件；

5、git commit -m "",将暂存区**所有的文件**弄到下一个节点

commit，将暂存区的文件持久化（他讲的）

6、删的文件也需要用git add加入暂存区，暂存区需要提交吧；删的文件没有放入暂存区可以回滚回来,	也可回滚版本（挺好玩）

7、**注意**：管理版本在本地就可以，不需要用到云端。

8、AC Terminal赋值时ctrl+insert

9、暂存区是所有分支共用的

10、git merge dev    这个合并其实是将head直接指向dev分支**#合并发生在持久化以后#，**若发生冲突需要进入文件，手动修改，在commit

11、将云端分支单独拉到本地分支，需要先建立一个对应分支，再用git branch --set-upstream-to=origin/branch_name1 branch_name2：将远程的branch_name1分支与本地的branch_name2分支对应相连，再用git pull，**注意，相对应可直接用git push ，不对应可用git push origin 分支名** 

**git push推向云端**



