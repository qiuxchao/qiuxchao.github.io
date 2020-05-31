---
title: 使用Git进行版本控制
date: 2019-12-09 08:08:08
img:
# top: 近期更新
categories: Git
tags: Git
---

# 使用Git进行版本控制
版本控制软件让我们能够拍摄处于可行状态的项目的快照。修改项目（如实现新功能）后，如果项目不能正常运行，可恢复到前一个可行状态。

通过使用版本控制软件，我们可以无忧无虑地改进项目，不用担心项目因我们犯了错而遭到破坏。对大型项目来说，这显得尤其重要，但对于较小的项目，哪怕是只包含一个文件的程序，这也大有裨益。

 在这篇文章中，我们将学习如何安装 **Git**，以及如何使用它来对当前开发的程序进行版本控制。
 **Git** 是当前最流行的版本控制软件，它包含很多高级工具，可帮助团队协作开发大型项目，但其最基本的功能也非常适合独立开发人员使用。
 **Git** 通过跟踪对项目中每个文件的修改来实现版本控制，如果你犯了错，只需恢复到保存的前一个状态即可。

## 安装Git
**Git** 可在所有操作系统上运行，但其安装方法因操作系统而异。
接下来的几节说明了如何在各种操作系统中安装它。
### 在 Windows 系统中安装 Git
要在 Windows 系统中安装 **Git**，请访问 [http://msysgit.github.io/](http://msysgit.github.io/) ，并单击 Download 。
### 在 Linux 系统中安装 Git
要在 Linux 系统中安装 **Git**，请执行如下命令：

```bash
$ sudo apt-get install git
```
这就成了。我们现在可以在项目中使用 **Git** 了。

### 配置 Git
**Git** 跟踪谁修改了项目，哪怕参与项目开发的人只有一个。为此，**Git** 需要知道我们的用户名和电子邮件地址。必须提供用户名，但可以使用虚构的电子邮件地址：

```bash
$ git config --global user.name "username"
$ git config --global user.email "username@example.com"
```
如果你忘记了这一步，在你首次提交时，**Git** 将提示你提供这些信息。
## 创建项目
我们来创建一个要进行版本控制的项目。
在系统中创建一个文件夹，并将其命名为 *git_practice* 。在这个文件夹中，创建一个简单的 Python 程序：
**hello_world.py**
```python
print("Hello Git world!")
```
我们将使用这个程序来探索 **Git** 的基本功能。
## 忽略文件
如果有扩展名为 *.pyc* 的文件，这是根据 *.py* 文件自动生成的，因此我们无需让 **Git** 跟踪它们。
这些文件存储在目录__pycache__中。为让 **Git** 忽略这个目录，创建一个名为 *.gitignore* 的特殊文件（这个文件名以句点打头，且没有扩展名），并在其中添加下面一行内容：
**.gitignore**
```bash
__pycache__/
```
这让 **Git** 忽略目录__pycache__中的所有文件。使用文件 .*gitignore* 可避免项目混乱，开发起来更容易。

你可能需要修改文本编辑器的设置，使其显示隐藏的文件，这样才能使用它来打开文件 *.gitignore* 。有些编辑器被设置成忽略名称以句点打头的文件。
## 初始化仓库
我们创建了一个目录，其中包含一个 *Python* 文件和一个 *.gitignore* 文件，可以初始化一个 **Git** 仓库了。为此，打开一个终端窗口，切换到文件夹 *git_practice*，并执行如下命令：
```bash
git_practice$ git init
Initialized empty Git repository in git_practice/.git/
git_practice$
```
输出表明 **Git** 在文件夹 *git_practice* 中初始化了一个空仓库。仓库是程序中被 **Git** 主动跟踪的一组文件。
**Git** 用来管理仓库的文件都存储在隐藏的 **.git/** 中，我们根本不需要与这个目录打交道，但千万不要删除这个目录，否则将丢弃项目的所有历史记录。
## 检查状态
执行其他操作前，先来看一下项目的状态：

```bash
git_practice$ git status
# On branch master
#
# Initial commit
#
# Untracked files:
# (use "git add <file>..." to include in what will be committed)
#
# .gitignore
# hello_world.py
#
nothing added to commit but untracked files present (use "git add" to track)
git_practice$
```
在 **Git** 中，**分支** 是项目的一个版本。从输出 “On branch master” 可知，我们位于分支 **master** 上。每次查看项目的状态时，输出都将指出我们位于分支 **master** 上。接下来的输出表明，我们将进行初始提交。**提交** 是项目在特定时间点的快照。
**Git** 指出了项目中未被跟踪的文件（Untracked files:），因为我们还没有告诉它要跟踪哪些文件。接下来，我们被告知没有将任何东西添加到当前提交中（nothing added to commit），但我们可能需要将未跟踪的文件加入到仓库中。
## 将文件加入到仓库中
下面将这两个文件加入到仓库中，并再次检查状态：
```bash
git_practice$ git add . 
git_practice$ git status
# On branch master
#
# Initial commit
#
# Changes to be committed:
# (use "git rm --cached <file>..." to unstage)
#
# new file: .gitignore
# new file: hello_world.py
#
git_practice$
```
命令 **git add .** 将项目中未被跟踪的所有文件都加入到仓库中。它不提交这些文件，而只是让 **Git** 开始关注它们。
现在我们使用命令 **git status** 检查项目的状态时，发现 Git 找出了需要提交的一些修改。标签 “new file” 意味着这些文件是新添加到仓库中的。
## 执行提交
下面来执行第一次提交：
```bash
git_practice$ git commit -m "Started project."
[master (root-commit) c03d2a3] Started project.
 2 files changed, 1 insertion(+)
 create mode 100644 .gitignore
 create mode 100644 hello_world.py 
git_practice$ git status
# On branch master
nothing to commit, working directory clean
git_practice$
```
我们执行命令 **git commit -m "message"** 以拍摄项目的快照。标志 **-m** 让Git将接下来的消息（ "Started project." ）记录到项目的历史记录中。输出表明我们在分支**master**上（ On branch master），且工作目录是干净的（nothing to commit, working directory clean）。这是我们每次提交项目的可行状态时都希望看到的消息。如果显示的消息不是这样的，请仔细阅读，很可能是在提交前忘记了添加文件。
## 查看提交历史
**Git** 记录所有的项目提交。下面来看一下提交历史：
```bash
git_practice$ git log
commit a9d74d87f1aa3b8f5b2688cb586eac1a908cfc7f
Author: Eric Matthes <eric@example.com>
Date:   Sun Dec 8 17:25:09 2019 +0800
Started project.
git_practice$
```
每次提交时，**Git** 都会生成一个包含40字符的独一无二的引用 **ID**。它记录提交是谁执行的、提交的时间以及提交时指定的消息。并非在任何情况下都需要所有这些信息，因此Git提供了一个选项，让我们能够打印提交历史条目的更简单的版本：
```bash
git_practice$ git log --pretty=oneline
a9d74d87f1aa3b8f5b2688cb586eac1a908cfc7f Started project.
git_practice$
```
标志 **--pretty=oneline** 指定显示两项最重要的信息：****提交的引用ID以及为提交记录的消息**** 。
## 第二次提交
为展示版本控制的强大威力，我们需要对项目进行修改，并提交所做的修改。为此，我们在 *hello_world.py* 中再添加一行代码：
**hello_world.py**
```python
print("Hello Git world!")
print("Hello everyone.")
```
如果我们现在查看项目的状态，将发现Git注意到了这个文件发生了变化：
```bash
git_practice$ git status
# On branch master
# Changes not staged for commit:
# (use "git add <file>..." to update what will be committed)
# (use "git checkout -- <file>..." to discard changes in working directory)
# 
# modified: hello_world.py
# 
no changes added to commit (use "git add" and/or "git commit -a")
git_practice$
```
输出指出了我们当前所在的分支（On branch master）、被修改了的文件的名称（modified: hello_world.py），还指出了所做的修改未提交（no changes added to commit）。
下面来提交所做的修改，并再次查看状态：
```bash
git_practice$ git commit -am "Extended greeting."
[master 08d4d5e] Extended greeting.
1 file changed, 1 insertion(+)
git_practice$ git status
# On branch master
nothing to commit, working directory clean 
git_practice$ git log --pretty=oneline
08d4d5e39cb906f6cff197bd48e9ab32203d7ed6 Extended greeting.
be017b7f06d390261dbc64ff593be6803fd2e3a1 Started project.
git_practice$
```
我们再次执行了提交，并在执行命令 **git commit** 时指定了标志 **-am**（git commit -am）。标志 **-a** 让 **Git** 将仓库中所有修改了的文件都加入到当前提交中（如果在两次提交之间创建了新文件，可再次执行命令 **git add .** 将这些新文件加入到仓库中）。标志 **-m** 让 **Git** 在提交历史中记录一条消息。
我们查看项目的状态时，发现工作目录也是干净的（nothing to commit, working directory clean）。
最后，我们发现提交历史中包含两个提交。
## 撤销修改
下面来看看如何放弃所做的修改，恢复到前一个可行状态。为此，首先在 *hello_world.py* 中再添加一行代码：
**hello_world.py**
```python
print("Hello Git world!")
print("Hello everyone.")
print("Oh no, I broke the project!")
```
保存并运行这个文件。
我们查看状态，发现 **Git** 注意到了所做的修改：
```bash
git_practice$ git status
# On branch master
# Changes not staged for commit:
# (use "git add <file>..." to update what will be committed)
# (use "git checkout -- <file>..." to discard changes in working directory)
#
# modified: hello_world.py
#
no changes added to commit (use "git add" and/or "git commit -a")
git_practice$
```
**Git** 注意到我们修改了 *hello_world.py*（ modified: hello_world.py）。我们可以提交所做的修改，但这次我们不提交所做的修改，而要恢复到最后一个提交（我们知道，那次提交时项目能够正常地运行）。为此，我们不对 *hello_world.py* 执行任何操作——不删除刚添加的代码行，也不使用文本编辑器的撤销功能，而在终端会话中执行如下命令：
```bash
git_practice$ git checkout .
git_practice$ git status
# On branch master
nothing to commit, working directory clean
git_practice$
```
命令 **git checkout** 让我们能够恢复到以前的任何提交。命令 **git checkout .** 放弃最后一次提交后所做的所有修改，将项目恢复到最后一次提交的状态。
如果我们返回到文本编辑器，将发现 *hello_world.py* 被修改成了下面这样：
```python
print("Hello Git world!")
print("Hello everyone.")
```
就这个项目而言，恢复到前一个状态微不足道，但如果我们开发的是大型项目，其中数十个文件都被修改了，那么恢复到前一个状态，将撤销自最后一次提交后对这些文件所做的所有修改。
这个功能很有用：实现新功能时，可以根据需要做任意数量的修改，如果这些修改不可行，可撤销它们，而不会对项目有任何伤害。你无需记住做了哪些修改，因而不必手工撤销所做的修改，**Git** 会替你完成所有这些工作。
## 检出以前的提交
我们可以检出提交历史中的任何提交，而不仅仅是最后一次提交，为此可在命令 **git check** 末尾指定该提交引用 **ID** 的 **前6个字符**（而不是句点）。通过检出以前的提交，就可以对其进行审核，然后返回到最后一次提交，或者放弃最近所做的工作，并选择以前的提交：
```bash
git_practice$ git log --pretty=oneline
08d4d5e39cb906f6cff197bd48e9ab32203d7ed6 Extended greeting.
be017b7f06d390261dbc64ff593be6803fd2e3a1 Started project.
git_practice$ git checkout be017b
Note: checking out 'be017b'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

	git checkout -b new_branch_name

HEAD is now at be017b7... Started project.
git_practice$
```
检出以前的提交后，我们将离开分支**master**，并进入 **Git** 所说的分离头指针（detached HEAD）状态，之所以说我们处于分离状态，是因为我们离开了一个命名分支（这里是 master）。
要回到分支 **master** ，可以检出它：
```bash
git_practice$ git checkout master
Previous HEAD position was be017b7... Started project.
Switched to branch 'master'
git_practice$
```
命令 **git checkout master** 让我们回到分支 **master** 。除非要使用 **Git** 的高级功能，否则在检出以前的提交后，最好不要对项目做任何修改。
然而，如果参与项目开发的人只有你自己，而你又想放弃较近的所有提交，并恢复到以前的状态，也可以将项目重置到以前的提交。为此，可在处于分支 **master** 上的情况下，执行如下命令：
```bash
git_practice$ git status
# On branch master
nothing to commit, working directory clean 
git_practice$ git log --pretty=oneline
08d4d5e39cb906f6cff197bd48e9ab32203d7ed6 Extended greeting.
be017b7f06d390261dbc64ff593be6803fd2e3a1 Started project. 
git_practice$ git reset --hard be017b
HEAD is now at be017b7 Started project. 
git_practice$ git status
# On branch master
nothing to commit, working directory clean 
git_practice$ git log --pretty=oneline
be017b7f06d390261dbc64ff593be6803fd2e3a1 Started project.
git_practice$
```
我们首先查看了状态，确认我们在分支 **master** 上（git status）。
查看提交历史时，我们看到了两个提交（git log --pretty=oneline）。
接下来，我们执行命令  **git reset --hard**，并在其中指定了要永久地恢复到提交的引用 **ID** 的前 **6** 个字符（git reset --hard be017b）。
再次查看状态，发现我们在分支 **master** 上，且没有需要提交的修改（git status）。
再次查看提交历史时，发现我们处于要从它重新开始的提交中（git log --pretty=oneline）。
## 删除仓库
有时候，仓库的历史记录被我们搞乱了，而我们又不知道如何恢复。如果无法恢复且参与项目开发的只有一个人，可继续使用这些文件，但要将项目的历史记录删除——删除目录 **.git**。这不会影响任何文件的当前状态，而只会删除所有的提交，因此我们将无法检出项目的其他任何状态。

为此，可打开一个文件浏览器，并将目录 **.git** 删除，也可通过命令行完成这个任务。这样做后，需要重新创建一个仓库，以重新对修改进行跟踪。下面演示了如何在终端会话中完成这个过程：

```bash
git_practice$ git status
# On branch master
nothing to commit, working directory clean
git_practice$ rmdir /s .git
git_practice$ git status
fatal: Not a git repository (or any of the parent directories): .git
git_practice$ git init
Initialized empty Git repository in git_practice/.git/ 
git_practice$ git status
# On branch master
#
# Initial commit
#
# Untracked files:
# (use "git add <file>..." to include in what will be committed)
#
# .gitignore
# hello_world.py
#
nothing added to commit but untracked files present (use "git add" to track)
git_practice$ git add .
git_practice$ git commit -m "Starting over."
[master (root-commit) 05f5e01] Starting over.
2 files changed, 2 insertions(+)
create mode 100644 .gitignore
create mode 100644 hello_world.py
git_practice$ git status
# On branch master
nothing to commit, working directory clean
git_practice$
```
我们首先查看了状态，发现工作目录是干净的（git status）。接下来，我们使用命令 **rmdir -rf .git** 删除了目录 **.git**。删除文件夹 **.git** 后，当我们再次查看状态时，被告知这不是一个 **Git** 仓库（git status）。**Git** 用来跟踪仓库的信息都存储在文件夹 **.git** 中，因此删除该文件夹也将删除整个仓库。

接下来，我们使用命令 **git init** 新建一个全新的仓库。然后，我们查看状态，发现又回到了初始状态，等待着第一次提交（git status）。我们将所有文件都加入仓库，并执行第一次提交（git add . | git commit -m "Starting over."）。然后，我们再次查看状态，发现我们在分支 **master** 上，且没有任何未提交的修改（git status）。

需要经过一定的练习才能学会使用版本控制，但一旦开始使用，我们就再也离不开它。
