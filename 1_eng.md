<div align="center">
   <h1>Multi-person collaboration document operation guide</h1>
</div>


## Git Technology Overview

Git is a distributed version control system designed to handle projects of any size with speed and efficiency. It allows multiple developers to collaborate on the same code base, tracking changes and promoting collaboration.

### Core Idea

- **Distributed Version Control**: Unlike centralized version control systems, each directory of Git is a complete warehouse on each computer, with complete history records and comprehensive version tracking capabilities, and does not rely on the network access or central server.

- **Snapshot**: Git captures project status through snapshots. Every time you commit, Git takes a picture of what all the files look like at that time, and stores a reference to that snapshot.

- **Branch**: A Git branch is actually a pointer to a snapshot of changes. When you branch a project, you are creating an environment where you can try out new ideas without affecting the main project.

### Core Components

- **1. Repository** Git is a distributed version control system whose main job is to manage code warehouses. A repository contains the complete history of the project and a snapshot of all files.

- **2. Working Directory** The workspace is the directory you are currently working in and contains the actual contents of the project files.

- **3. Staging Area** The staging area is a place where changes are temporarily stored in preparation for submission to the repository.

- **4. Repository** The repository is the most important part of Git, including commit records, branches, tags and other information.

- **5. Commit** Commit is the most basic operation in Git, which is used to save the current status of the working directory to the repository.

- **6. Branch** A branch is an independent line used to develop new features. It allows you to modify and experiment with the code without affecting the main line.

- **7. Tag** The tag is a name for a specific version of the code, usually used for releases or important milestones.

- **8. Remote Repository** Remote warehouse is a Git warehouse hosted on the network, such as GitHub, GitLab, etc., used for team collaboration and code sharing.

- **9. Clone** The clone operation is used to copy the project from the remote warehouse to the local one, creating an identical copy of the remote warehouse.

- **10. Pull and Push** The pull operation is to obtain the latest content from the remote warehouse to the local one, and the push operation is to synchronize the local submissions to the remote warehouse.

- **11. Merge and Rebase** Merge is to merge the modifications of different branches together, while rebasing is to move the commits of the current branch to another branch and re-apply them.

- **12. Conflict Resolution** When conflicts occur during the merge operation, you need to manually resolve the conflicts and then submit the resolved code.

### work process
Git has three states, and your file may be in one of them: committed, modified, and staged.
- Modified means that the file has been modified but has not been saved to the database.
- Staged means that the current version of a modified file has been marked to be included in the next committed snapshot.
- Committed means the data has been safely saved in the local database.
![This is an image](https://git-scm.com/book/en/v2/images/areas.png)

The basic Git workflow is as follows:
- Modify files in the workspace.
- Selectively stage the changes you want to commit next so that only the changed parts are added to the staging area.
- Submit the update, find the files in the staging area, and permanently store the snapshot in the Git directory.
![alt text](https://img-blog.csdn.net/20150919155324383)

Our workflow is roughly as follows:
- It should be noted that we do not need Fork, we only need to push to our own branch, and finally pull request to the main branch, which is more centralized and convenient.
![alt text](https://github.com/liyinred/Test1/blob/main/pic/a7360af316c8947b612be2e2128b128.jpg?raw=true)

Improved image![This is an image](https://github.com/liyinred/Test1/blob/main/pic/aca87e17097ca16c38c4a8150775976.jpg?raw=true)

## Preparation
- **Install Git** [官网](https://github.com/git-for-windows/git/releases/download/v2.44.0.windows.1/Git-2.44.0-64-bit.exe) **+** [详细教程](https://blog.jiumoz.com/archives/git-an-zhuang-xiang-jie)
- **Create a Github account** [注册链接](https://github.com/login?add_account=1&return_to=https%3A%2F%2Fgithub.com%2F)

# The following is a specific example of a multi-person collaboration document
## 1. Leader invites Collaborator to join the project and Collaborator accepts the invitation
- Suppose A creates a new GitHub repository named Test1 and invites Collaborator to enter
- Collaborator logs in to the GitHub homepage.
- Click the "notifications" button in the upper right corner, click the notification and accept the invitation. At this time, Collaborator appears in Leader's "Collaborators".
![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412091411.png?raw=true)![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412091428.png?raw=true)![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412091442.png?raw=true)![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412090204.png?raw=true)

## 2. Clone Repository

Assume that B and C are other members of the project team. They first need to clone the repository to their local machine. The clone link can be obtained through the repository page on GitHub. ![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412103938.png?raw=true)After creating your own project folder, open Git Bash and clone the repository to your local computer.

```bash
cd /D/test/Git_test_collaborator_Wenhao  #  切换到自己的项目路径
git clone https://github.com/liyinred/Test1.git  # 从远程仓库克隆一个版本库到本地
cd Test1  #  切换到本地仓库的文件夹
```
![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412104552.png?raw=true)

After that, you can see the files of the main branch of the warehouse in the local warehouse ![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412140137.png?raw=true)

## 3. Create Branches and Edit Documentation

Suppose B decides to add a new project introduction document, he creates a new branch and starts editing. After writing the file locally and placing it in the local warehouse folder, perform the following operations in GitBash:

```bash
git checkout -b add_lwh  #创建并切换到add_lwh分支
git add introduction.md  #将刚刚编写好的introduction.md文件添加
git commit -m "Add project introduction"  #  确认添加并写入备注'Add project introduction'
```
![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412112215.png?raw=true)

Similarly, suppose C wants to update the template1.tex file in the warehouse and also create a new branch to work on. After rewriting the file locally and placing it in the local warehouse folder, perform the following operations in Git Bash:

```bash
git checkout -b update-readme
git add README.md
git commit -m "Update README file"
```

## 4. Push Changes (Push)
B and C respectively push their changed branches to GitHub

```bash
# 在B中的Git Bash中操作
git push origin add_lwh

# C中的Git Bash中操作
git push origin update-readme
```
![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412112644.png?raw=true)

Afterwards, you can see the branch you created in the Github project repository![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412112800.png?raw=true)
## 5. Initiate and Merge Branches Pull Request

B and C respectively initiate Pull Requests for their branches on GitHub. A, as the project maintainer, reviews these changes and decides to merge them into the master branch.

Click the buttons framed below![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412113105.png?raw=true)

Modify compare here to your own branch name, you can view its changes, and then Create![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412113143.png?raw=true)

Fill in the title (standard format) and description (standard format) here, and then Create![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412113341.png?raw=true)

You can see this Pull request on the Leader side, and you can decide whether to merge it into the main branch![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412113444.png?raw=true)

## 6. Pull the Latest Master Branch Changes
After merging the changes of B and C, other members need to update their local master branches, also using Git Bash in the local warehouse directory:

```bash
git checkout main  #  先切换成分支
git pull origin main  #  获取更新
```
![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412113903.png?raw=true)
## 7. Rebase Operation (Rebase)

Suppose A has made some commits on the main branch and updated it, and B wants to continue working on the basis of these changes. He can use the rebase operation to update his branch.

```bash
git checkout add_lwh
git rebase main
```

If a conflict is encountered during the rebase process, Git will pause the rebase and let B resolve the conflict. After resolving the conflict, B continues the rebasing process:

```bash
git add introduction.md
git rebase --continue
```
Eventually, B can push his changes to GitHub again (may need to use a force push since the history has been changed):

```bash
git push origin add_lwh --force
```
![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412135404.png?raw=true)

## 8.View Specific Changes and Comments

Assume that in the process of writing the manual, A, B, and C each submitted their own modifications at different times and left relevant comments.

```bash
git log  #  查看所有提交日志和comment：

git log --follow -p "C:\Users\liwh\Desktop\晨辰医药\5 week\data-structure\1.md"  #  查看具体路径下的文件所有更改日志以及详细的修改内容
```
![image](https://github.com/liyinred/Git_Wenhao/assets/83255231/4e2e4b32-d9d3-40f5-a8ff-312827f95895)![image](https://github.com/liyinred/Git_Wenhao/assets/83255231/c082aeed-0586-461e-a33d-749d66211a35)

During the manual writing process, team members may need to compare the differences between two different versions to understand the impact of each person's changes on the final document. For example, suppose a team member wants to compare the differences between the initial draft submitted by A and the updated version submitted by B. At this point, they can use the command **git diff initial-commit-hash updated-commit-hash** to view the specific differences in the file between the two versions to better understand the impact of each person's modifications on the document.

```bash
git diff ecc734c6a48f74675872c6ec37e5848657b972d0 5fa40125be76eb0c4be7d27b2854c18e04bd5e35  #  查看两个不同提交中的所有文件差异
````
![image](https://github.com/liyinred/Git_Wenhao/assets/83255231/78f71f30-a82c-43d7-bccb-8fb4d3af4c87)

在手册编写的过程中，团队成员可能也需要查看某次提交与其上一次提交之间的具体差异。例如，假设 C 想要查看自己完成的最后修订与上一次提交之间的具体修改内容。这时，他可以使用命令 **git diff last-commit-hash^ last-commit-hash** 来查看这两次提交之间文件的详细差异，以便更好地了解自己的修改对文档的影响。
```bash
git diff 5fa40125be76eb0c4be7d27b2854c18e04bd5e35^ 5fa40125be76eb0c4be7d27b2854c18e04bd5e35  #  查看查看某次提交和它上次提交(^)的详细文件差异
```
![image](https://github.com/liyinred/Git_Wenhao/assets/83255231/21fcfb8a-33d4-422d-b611-88f18091feaa)

## 9.Solution to the problem that local files cannot be pushed to Github

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

[Solve the "error: failed to push some refs to" error in Git Push](https://blog.csdn.net/Tester_muller/article/details/132837267)

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
