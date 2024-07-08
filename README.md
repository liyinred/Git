<div align="center">
   <h1>多人协作文档操作 Manual</h1>
   <a href="https://github.com/liyinred/Git_Wenhao/blob/main/1_eng.md" target="_blank" style="font-size: 30px;">English Version</a>
</div>


<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

  - [Git 技术概览](#git-技术概览)
    - [核心概念](#核心概念)
    - [核心组件](#核心组件)
    - [工作流程](#工作流程)
  - [准备前提](#准备前提)
- [以下是一个进行多人协作文档的具体例子](#以下是一个进行多人协作文档的具体例子)
  - [1. Leader邀请Collaborator加入该项目和Collaborator接受邀请](#1-leader邀请collaborator加入该项目和collaborator接受邀请)
  - [2. 克隆仓库](#2-克隆仓库)
  - [3. 创建分支和编辑文档](#3-创建分支和编辑文档)
  - [4. 推送更改 (Push)](#4-推送更改-push)
  - [5. 发起和合并分支 Pull Request](#5-发起和合并分支-pull-request)
  - [6. 拉取最新的主分支更改](#6-拉取最新的主分支更改)
  - [7. 变基操作 (Rebase)](#7-变基操作-rebase)
  - [8.查看具体修改和评论](#8查看具体修改和评论)
  - [9.本地文件Push不了到Github的问题解决方法](#9本地文件push不了到github的问题解决方法)

<!-- /code_chunk_output -->


## Git 技术概览

Git 是一个分布式版本控制系统，设计用来以高速和高效率处理任何规模的项目。它允许多个开发者在同一个代码库上协作，跟踪更改并促进合作。

### 核心概念

- **分布式版本控制**：与集中式版本控制系统不同，Git 的每一个目录在每台电脑上都是一个完整的仓库，拥有完整的历史记录和全面的版本跟踪能力，不依赖网络访问或中央服务器。

- **快照**：Git 通过快照来捕捉项目状态。每次提交时，Git 都会对当时所有文件的样子进行拍照，存储对那个快照的引用。

- **分支**：Git 分支实际上是对更改快照的一个指针。创建项目分支时，你就在创建一个环境，在这里可以尝试新想法而不影响主项目。

### 核心组件

- **1. 仓库（Repository）**
  Git 是一个分布式版本控制系统，主要工作是管理代码仓库。一个仓库包含着项目的完整历史记录和所有文件的快照。

- **2. 工作区（Working Directory）**
  工作区是你当前正在工作的目录，包含项目文件的实际内容。

- **3. 暂存区（Staging Area）**
  暂存区是一个临时存放改动的地方，用来准备提交到版本库中。

- **4. 版本库（Repository）**
  版本库是Git最重要的部分，包括了提交（commit）记录、分支（branch）、标签（tag）等信息。

- **5. 提交（Commit）**
  提交是Git中最基本的操作，用于保存工作目录的当前状态到版本库中。

- **6. 分支（Branch）**
  分支是用来开发新功能的独立线路，它允许你在不影响主线的情况下进行代码的修改和实验。

- **7. 标签（Tag）**
  标签是对代码某个特定版本的命名，通常用于发布版本或重要的里程碑。

- **8. 远程仓库（Remote Repository）**
  远程仓库是托管在网络上的Git仓库，比如GitHub、GitLab等，用于团队协作和代码共享。

- **9. 克隆（Clone）**
  克隆操作用于从远程仓库复制项目到本地，创建一个与远程仓库相同的副本。

- **10. 拉取（Pull）和推送（Push）**
  拉取操作是从远程仓库获取最新内容到本地，推送操作是将本地的提交同步到远程仓库中。

- **11. 合并（Merge）和变基（Rebase）**
  合并是将不同分支的修改合并到一起，而变基是将当前分支的提交移动到另一个分支的基础上重新应用。

- **12. 冲突解决（Conflict Resolution）**
  当合并操作中出现冲突时，需要手动解决冲突，然后提交解决后的代码。

### 工作流程
 Git 有三种状态，你的文件可能处于其中之一： 已提交（committed）、已修改（modified） 和 已暂存（staged）。
- 已修改表示修改了文件，但还没保存到数据库中。
- 已暂存表示对一个已修改文件的当前版本做了标记，使之包含在下次提交的快照中。
- 已提交表示数据已经安全地保存在本地数据库中。
![This is an image](https://git-scm.com/book/en/v2/images/areas.png)

基本的 Git 工作流程如下：
- 在工作区中修改文件。
- 将你想要下次提交的更改选择性地暂存，这样只会将更改的部分添加到暂存区。
- 提交更新，找到暂存区的文件，将快照永久性存储到 Git 目录。
![alt text](https://img-blog.csdn.net/20150919155324383)

我们的工作流程大致如下：
- 需要注意的的是我们并不需要Fork,只需要push到自己的分支,最后向主分支 pull request 即可,这样更为集中和方便
![alt text](https://github.com/liyinred/Test1/blob/main/pic/a7360af316c8947b612be2e2128b128.jpg?raw=true)

改进后的图：
![This is an image](https://github.com/liyinred/Test1/blob/main/pic/aca87e17097ca16c38c4a8150775976.jpg?raw=true)

## 准备前提
- **安装好Git**  [官网](https://github.com/git-for-windows/git/releases/download/v2.44.0.windows.1/Git-2.44.0-64-bit.exe)  **+** [详细教程](https://blog.jiumoz.com/archives/git-an-zhuang-xiang-jie)
- **创建好Github账户** [注册链接](https://github.com/login?add_account=1&return_to=https%3A%2F%2Fgithub.com%2F)

# 以下是一个进行多人协作文档的具体例子
## 1. Leader邀请Collaborator加入该项目和Collaborator接受邀请
- 假设A创建了一个新的GitHub仓库名为 Test1,并邀请Collaborator进入
- Collaborator登录进入GitHub主页。
- 点击右上角的 "notifications" 按钮，点击该通知并接受邀请,这时Leader的“Collaborators”中出现了Collaborator.
![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412091411.png?raw=true)
![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412091428.png?raw=true)
![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412091442.png?raw=true)
![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412090204.png?raw=true)

## 2. 克隆仓库

假设B和C是项目团队的其他成员。他们首先需要将仓库克隆到本地计算机。这可以通过GitHub上的仓库页面获取到克隆链接。
![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412103938.png?raw=true)
创建好自己的项目文件夹后打开Git Bash将仓库克隆到本地计算机
```bash
cd /D/test/Git_test_collaborator_Wenhao  #  切换到自己的项目路径
git clone https://github.com/liyinred/Test1.git  # 从远程仓库克隆一个版本库到本地
cd Test1  #  切换到本地仓库的文件夹
```
![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412104552.png?raw=true)

之后在本地仓库就可以看到仓库主分支的文件了
![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412140137.png?raw=true)

## 3. 创建分支和编辑文档

假设B决定添加一个新的项目介绍文档，他创建一个新分支并开始编辑。在本地编写好文件并放入本地仓库文件夹后在GitBash进行下列操作:
```bash
git checkout -b add_lwh  #创建并切换到add_lwh分支
git add introduction.md  #将刚刚编写好的introduction.md文件添加
git commit -m "Add project introduction"  #  确认添加并写入备注'Add project introduction'
```
![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412112215.png?raw=true)

同理假设C同时想更新仓库中的 template1.tex 文件，也创建一个新分支进行工作。在本地改写好文件并放入本地仓库文件夹后在 Git Bash 进行下列操作:
```bash
git checkout -b update-readme
git add README.md
git commit -m "Update README file"
```

## 4. 推送更改 (Push)
B和C分别将他们的更改后的分支推送到GitHub
```bash
# 在B中的Git Bash中操作
git push origin add_lwh

# C中的Git Bash中操作
git push origin update-readme
```
![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412112644.png?raw=true)

之后便可在Github的项目仓库里面看到自己创建的分支
![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412112800.png?raw=true)
## 5. 发起和合并分支 Pull Request

B和C在 GitHub 上为他们的分支分别发起 Pull Request。A作为项目维护者审查这些更改，并决定合并它们到主分支。

依次点击下图框住的按钮
![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412113105.png?raw=true)

这里修改compare成自己的分支名,可查看其变化,再Create
![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412113143.png?raw=true)

这里填写标题(规范格式)和描述(规范格式),再Create
![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412113341.png?raw=true)

在Leader端便能看到这个Pull请求,可以决定是否将其Merge到主分支
![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412113444.png?raw=true)

## 6. 拉取最新的主分支更改
在合并了B和C的更改后，其他成员需要更新他们的本地主分支,同样是在本地仓库目录下使用Git Bash进行操作:
```bash
git checkout main  #  先切换成分支
git pull origin main  #  获取更新
```
![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412113903.png?raw=true)
## 7. 变基操作 (Rebase)

![image](https://github.com/liyinred/Git/assets/83255231/da34124e-0783-4f10-aca1-0b26d834621c)
假设A在主分支上做了一些提交就行了更新，而B希望在这些更改的基础上继续工作，他可以使用变基操作来更新他的分支(先要pull最新的main分支)。
```bash
git checkout add_lwh
git rebase main
```

如果在变基过程中遇到冲突，Git会暂停变基并让B解决冲突。解决冲突后，B继续变基过程：
```bash
git add introduction.md
git rebase --continue
```
最终，B可以将他的更改再次推送到GitHub（由于历史已被更改，可能需要使用强制推送）：
```bash
git push origin add_lwh --force
```
![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412135404.png?raw=true)

## 8.查看具体修改和评论

假设A、B、C 三人在完成manual的编写过程中，每个人都在不同的时间提交了自己的修改，并留下了相关的注释。
```bash
git log  #  查看所有提交日志和comment：

git log --follow -p "C:\Users\liwh\Desktop\晨辰医药\5 week\data-structure\1.md"  #  查看具体路径下的文件所有更改日志以及详细的修改内容
```
![image](https://github.com/liyinred/Git_Wenhao/assets/83255231/4e2e4b32-d9d3-40f5-a8ff-312827f95895)
![image](https://github.com/liyinred/Git_Wenhao/assets/83255231/c082aeed-0586-461e-a33d-749d66211a35)

在手册编写的过程中，团队成员可能需要比较两个不同版本之间的差异，以便了解每个人的修改对最终文档的影响。例如，假设团队成员想要比较 A 提交的初始草稿和 B 提交的更新版本之间的差异。这时，他们可以使用命令 **git diff initial-commit-hash updated-commit-hash** 来查看这两个版本之间文件的具体差异，从而更好地理解每个人的修改对文档的影响。
```bash
git diff ecc734c6a48f74675872c6ec37e5848657b972d0 5fa40125be76eb0c4be7d27b2854c18e04bd5e35  #  查看两个不同提交中的所有文件差异
````
![image](https://github.com/liyinred/Git_Wenhao/assets/83255231/78f71f30-a82c-43d7-bccb-8fb4d3af4c87)

在手册编写的过程中，团队成员可能也需要查看某次提交与其上一次提交之间的具体差异。例如，假设 C 想要查看自己完成的最后修订与上一次提交之间的具体修改内容。这时，他可以使用命令 **git diff last-commit-hash^ last-commit-hash** 来查看这两次提交之间文件的详细差异，以便更好地了解自己的修改对文档的影响。
```bash
git diff 5fa40125be76eb0c4be7d27b2854c18e04bd5e35^ 5fa40125be76eb0c4be7d27b2854c18e04bd5e35  #  查看查看某次提交和它上次提交(^)的详细文件差异
```
![image](https://github.com/liyinred/Git_Wenhao/assets/83255231/21fcfb8a-33d4-422d-b611-88f18091feaa)

## 9.本地文件Push不了到Github的问题解决方法
```bash
# 配置Git用户信息
git config --global user.name "你的用户名"
git config --global user.email "你的邮箱地址"

# 初始化本地Git仓库
git init

# 添加当前目录下所有文件到Git暂存区
git add .

# 提交更改到本地仓库
git commit -m "Initial commit"

# 连接到GitHub仓库，这里需要替换成你自己的GitHub仓库URL
git remote add origin https://github.com/你的用户名/你的仓库名.git

# 推送到GitHub，默认推送到master分支，如果是main分支则需修改为main
git push -u origin main
```

![image](https://github.com/liyinred/Git_Wenhao/assets/83255231/8f967baf-bc7b-4b78-978d-0c820e552fdf)

[解决 Git Push 出现 “error: failed to push some refs to“错误](https://blog.csdn.net/Tester_muller/article/details/132837267)
```bash
# 以下 host:port 指定是你当前代理使用的主机及端口号。例如：localhost:7890、127.0.0.1:7890 等

# 配置socks5代理
# git config --global http.proxy socks5 host:port
# git config --global https.proxy socks5 host:port

# 配置http代理
git config --global http.proxy host:port
git config --global https.proxy host:port

git push --force origin main

```

步骤一：项目初始化
- A本地创建Django框架：A(项目主导者)在本地创建好Django框架，并确保项目结构合理。
- 推送到GitHub主分支：A将项目推送到GitHub的main分支，确保包括requirements.txt文件。
- GitHub中更新README：A在README.md文件中详细说明项目的结构和工作流程，以便团队成员了解项目的基本信息。
  
步骤二：任务分配
- 功能需求描述：当A需要B实现一个新功能时(比如仓库系统需要实现fetch同步功能)，A通过邮件详细描述需要实现的功能，包括功能的目的、预期的实现方式和具体的技术要求。

步骤三：分支操作
- 拉取主分支：B接到任务后，从GitHub上拉取main分支到本地。
- 创建新分支：B在本地创建一个新的分支，用于开发新功能。例如，分支命名可以为feature/功能描述。

步骤四：开发与提交
- 开发新功能：B在本地分支中进行代码修改和功能实现。
- 注释代码：B在修改和新增的代码部分加上详细的注释，确保代码易于理解和维护。

步骤五：代码合并与审核
- 创建Pull Request：B完成功能开发后，将本地分支推送到GitHub中的分支，并创建一个Pull Request，详细说明修改的内容和功能实现情况。
- 代码审核与测试：A在收到Pull Request后，进行代码审核和测试。如果功能符合预期，A同意并合并Pull Request；如果不符合预期，A拒绝Pull Request。

步骤六：反馈与修改
- 反馈问题：A在拒绝Pull Request时，通过邮件详细说明未能通过审核的具体问题，并提供改进建议。
- 重复开发与提交：B根据A的反馈，重新修改代码，直至功能符合预期。
  
![image](https://github.com/liyinred/Git_Wenhao/assets/83255231/e2f9bb67-ce18-41b3-b87c-6817f22e7c86)
