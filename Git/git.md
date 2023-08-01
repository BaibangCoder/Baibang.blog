# Git分布式管理控制工具

主要作用场景：备份、代码还原、协同开发、追随问题的编写人和编写时间。

分布式版本控制系统没有“中央服务器”，每个人的电脑都是一个完整的版本库，这样工作的时候，无需要联网了，因为版本库就在你自己的电脑上，多人协作只需要各自的修改推送给对方，就能互相看到对方的修改了。

<img src="E:\Code\GitHubProject\Git\assets\image-20230629213851072.png" alt="image-20230629213851072" style="zoom: 67%;" />

## git的工作流程图

<img src="E:\Code\GitHubProject\Git\assets\image-20230629214514513.png" alt="image-20230629214514513" style="zoom:67%;" />

命令如下：

- 1.clone(克隆)：从远程仓库中克隆代码到本地仓库
- 2.checkout(检出)：从本地仓库中检出一个仓库分支然后进行修订
- 3.add(添加)：在提交前先将代码提交到暂存区
- 4.commit(提交)：提交到本地仓库。本地仓库中保存修改的各个历史版本
- 5.fetch(抓取)：从远程库，抓取到本地库，不进行任何的合并动作，一般操作比较少。
- 6.pull(拉取)：从远程库拉到本地库，自动进行合并(merage)，然后放到工作区，相当于fetch+merge
- 7.push(推送)：修改完成后，需要和团队共享代码时，将代码推送到远程仓库

# Git安装与常用命令

![image-20230629215753081](E:\Code\GitHubProject\Git\assets\image-20230629215753081.png)

直接从官网下载，里面有教程

下载后看到这两个菜单则说明Git安装成功



**备注**：

- Git GUI：Git提供的图形界面工具
- Git Bash：Git提供的命令行工具

当==安装Git后首先要做的事情是设置用户名称和email地址==。这是非常重要的，因为每次Git提交都会使用该用户的信息

## 基本配置

1. 打开Git Bash

2. 设置用户信息

   git config --global user.name"用户名"

   git config --global user.email"邮箱"

​	查看配置信息

​		git config --global user.name

​		git config --global user.email

**注意**：用户名和邮箱输入错误不要紧，重新来一遍就行，邮箱不需要是可用邮箱

<img src="E:\Code\GitHubProject\Git\assets\image-20230708211305952.png" alt="image-20230708211305952" style="zoom:67%;" />

## 为常用指令配置别名（可选）

有些常用的指令参数非常多，每次都要输入好多参数，我们可以使用别名。

1. 打开用户目录，创建`.bashrc`文件

   用户目录的地址就是C盘用户里面的名字为用户名的文件夹

   部分windows系统不允许创建点号开头的文件，可以打开gitBash,执行`touch ~/.bashrc`

   <img src="E:\Code\GitHubProject\Git\assets\image-20230629223127495.png" alt="image-20230629223127495" style="zoom:67%;" />

2. 在`.bashrc`文件中输入以下内容：

   ```Python
   # 用于输出git提交日志
   alias git-log='git log --pretty=oneline --all --graph --abbrev-commit'
   # 用于输出当前目录所有文件的基本信息
   alias ll='ls -al'
   ```

3. 打开gitBash，执行`source ~/.bashrc`

   <img src="E:\Code\GitHubProject\Git\assets\image-20230629223807228.png" alt="image-20230629223807228" style="zoom:67%;" />

4. 解决GitBash乱码的问题

   1. 打开Git Bash执行下面命令

      ```
      git config --global core.quotepath false
      ```

   2. 然后执行这步骤操作

      ![image-20230629224105890](E:\Code\GitHubProject\Git\assets\image-20230629224105890.png)

## 获取本地仓库

要进行版本控制，首先需要获得本地仓库。

1. 在电脑的任意位置创建一个空目录作为本地Git库。
2. 进入目录中，右键打开Git bash窗口。
3. 执行`git init`命令。
4. 创建成功后可在文件夹下看到隐藏的.git目录。

<img src="E:\Code\GitHubProject\Git\assets\image-20230708212523615.png" alt="image-20230708212523615" style="zoom:67%;" />

**概念**：文件夹里面除了.git文件夹外都是工作目录。

## 基础操作指令

Git工作目录下对于文件的修改会存在几个状态，这些修改的状态会随着我们执行Git的命令而发生变化。

<img src="E:\Code\GitHubProject\Git\assets\image-20230708212921757.png" alt="image-20230708212921757" style="zoom:67%;" />

- `git status`  查看修改的状态（暂存区、工作区）

- `git add 单个文件名 | 通配符.` 将所有修改加入暂存区

- `git commit -m '注释内容' ` 提交暂存区的内容到本地仓库的当前分支

- `git log [option]` 查看提交日志

  --all 显示所有分支

  --pretty=oneline 将提交信息显示为一行

  --abbrev-commit 使得输出的commitld更简短

  --graph 以图的形式显示

**版本回退**

作用：版本切换

命令形式：`git reset --hard commitID`

​		commitID 可以使用`git log`来查看

如何查看已经删除的记录？

`git reflog` 这个指令可以看到已经删除的提交记录

**添加文件至忽略列表**

如果在.git文件目录同级的目录中有不希望被git跟踪的文件，就可以在工作目录中创建一个名为.gitignore 的文件（文件名称固定），列出要忽略的文件模式。

 <img src="E:\Code\GitHubProject\Git\assets\image-20230708232829759.png" alt="image-20230708232829759" style="zoom:67%;" />

## 分支

`git branch` 查看有那些分支，使用`git-log`也可以查看，更清晰。

`git branch 分支名` 添加一个分支。

`git checkout 分支名` 切换分支。

`git checkout -b 分支名` 创建并切换到这个分支。

`git merge 分支名` 一个分支上的提交可以合并到另一个分支。

`git branch -d b1` 不能删除当前分支，只能删除其他分支，d为小写时做各种检查后删除，为大写时不做任何检查，强制删除。

<img src="E:\Code\GitHubProject\Git\assets\image-20230709091032539.png" alt="image-20230709091032539" style="zoom:67%;" />

<img src="E:\Code\GitHubProject\Git\assets\image-20230709091154578.png" alt="image-20230709091154578" style="zoom:67%;" />
