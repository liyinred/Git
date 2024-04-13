# A how-to guide for multi-person collaborative document

## Git Technology Overview

Git is a distributed version control system designed to handle projects of any size with high speed and efficiency. It allows multiple developers to work together on the same code base, tracking changes and facilitating collaboration.


### Core Concepts

- **Distributed version control** Unlike a centralized version control system, every directory in Git is a complete repository on every computer, with complete history and comprehensive version tracking capabilities, without relying on network access or a central server.

- **Snapshot** Git uses snapshots to capture project status. On each commit, Git takes a picture of what all the files look like at the time, storing a reference to that snapshot.

- **Branch** A Git branch is actually a pointer to a snapshot of changes. When you create a project branch, you are creating an environment where you can try out new ideas without affecting the main project.

### Core Components

- **1. Repository** Git is a distributed version control system whose main job is to manage code repositories. A repository contains a complete history of the project and a snapshot of all the files.

- **2. Working Directory** The workspace is the directory in which you are currently working and contains the actual contents of the project file.

- **3. Staging Area** The staging area is a temporary place to store changes in preparation for committing to the repository.

- **4. Repository** repository is the most important part of Git, including commit records, branches, tags, and so on.

- **5. Commit** Commit is the most basic operation in Git to save the current state of the working directory to the repository.

- **6. Branch** Branches are independent lines used to develop new functionality, allowing you to modify and experiment with code without affecting the mainline.

- **7. Tag** A label is a name for a particular version of code, usually used for a release or an important milestone.

- **8. Remote Repository** A remote repository is a Git repository hosted on a network, such as GitHub, GitLab, etc., for team collaboration and code sharing.

- **9. Clone** The clone operation is used to copy items from the remote repository to the local, creating a copy that is identical to the remote repository.

- **10. Pull and Push** pull operation is to get the latest content from the remote repository to the local, and the push operation is to synchronize the local submission to the remote repository.

- **11. Merge and Rebase** Merge is the merging together of modifications from different branches, while rebase is the moving of a commit from the current branch to be reapplied on the basis of another branch.

- **12. Conflict Resolution** When a conflict occurs during a merge operation, you need to manually resolve the conflict and then commit the resolved code.

### Workflow
**Git has three States, and your file can be in one of them: committed, modified, and staged.**
- Modified indicates that the file was modified but not yet saved to the repository.
- Staged indicates that the current version of a modified file is marked for inclusion in the next commit snapshot.
- Committed means that the data has been safely saved in the local repository.
![This is an image](https://git-scm.com/book/en/v2/images/areas.png)

**The basic Git workflow is as follows.**
- Modify the file in the workspace.
- Selectively stage the changes you want to commit the next time. This adds only the changes to the staging area.
- Commit the update, locate the files in the staging area, and permanently store the snapshot in the Git directory.
![alt text](https://img-blog.csdn.net/20150919155324383)

**Our workflow is roughly as follows.**
- It should be noted that we do not need to Fork, just push to their own branch, and finally to the master branch pull request can be, so more centralized and convenient !
![alt text](https://github.com/liyinred/Test1/blob/main/pic/a7360af316c8947b612be2e2128b128.jpg?raw=true)

**Improved graph** ![This is an image](https://github.com/liyinred/Test1/blob/main/pic/aca87e17097ca16c38c4a8150775976.jpg?raw=true)
## Prepare the premise
- **Install Git** [Install the package link and install it according to the default option.](https://github.com/git-for-windows/git/releases/download/v2.44.0.windows.1/Git-2.44.0-64-bit.exe)
- **Create a Github account** [Registration Link](https://github.com/login?add_account=1&return_to=https%3A%2F%2Fgithub.com%2F)

# The following is a concrete example of a multi-person collaborative document
## 1. Leader invites Collaborator to join the project and Collaborator accepts the invitation
- Suppose A creates a new GitHub repository called Test1 and invites the Collaborator in.
- Collaborator Log in to the GitHub homepage.
- Click the "Notifications" button in the upper right corner, click the notification and accept the invitation. At this time, Collaborator.
![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412091411.png?raw=true)![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412091428.png?raw=true)![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412091442.png?raw=true)![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412090204.png?raw=true)

## 2. Clone the repository

Assume that B and C are other members of the project team. They first need to clone the repository to the local machine. You can get a link to the clone from the repository page on GitHub. After creating your own project folder, open Git Bash to clone the repository to your local computer.
![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412103938.png?raw=true)

```bash
cd /D/test/Git_test_collaborator_Wenhao  # Switch to your own project path
git clone https://github.com/liyinred/Test1.git  # From a remote repository clone, a version library to the local area
cd Test1  # Folder to switch to the local repository
```
![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412104552.png?raw=true)

After that, you can see the files of the main branch of the repository in the local repository.
![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412140137.png?raw=true)

## 3. Creating Branches and Editing Document

Suppose B decides to add a new project introduction document, he creates a new branch and starts editing. After writing the file locally and putting it into the local repository folder, perform the following operations in GitBash:

```bash
git checkout -b add_lwh  # Create and switch to ADD_LWH branch
git add introduction.md  # Add the just -written IntRoduction.md file
git commit -m "Add project introduction"  # Confirm and write and write to the note 'add project intification'
```
![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412112215.png?raw=true)

Similarly, suppose that C also wants to update the template 1.tex file in the repository and create a new branch to work on. After rewriting the file locally and putting it in the local repository folder, do the following in Git Bash:

```bash
git checkout -b update-readme
git add README.md
git commit -m "Update README file"
```

## 4. Push Changes
B and C each push their changed branches to GitHub

```bash
# Operated in git bash in B
git push origin add_lwh

# C in git bash operation
git push origin update-readme
```
![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412112644.png?raw=true)

After that, you can see the branch you created in Github's project repository.
![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412112800.png?raw=true) 
## 5. Initiate and merge branch Pull requests

B and C each initiate a Pull Request for their branch on GitHub. A, as the project maintainer, reviews the changes and decides to merge them into the master branch.

Click the framed buttons in the figure below in turn ![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412113105.png?raw=true)

Modify compare here to its own branch name to view its change, and then Create ![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412113143.png?raw=true)

Fill in the title (canonical format) and description (canonical format) here, and then Create ![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412113341.png?raw=true)

You can see the Pull request on the Leader side and decide whether to Merge it to the master branch ![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412113444.png?raw=true)

## 6. Pull latest master branch Chan
After merging the changes for B and C, the other members need to update their local master branch, again using Git Bash under the local repository directory.

```bash
git checkout main  # Switch ingredients first
git pull origin main  # Get update
```
![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412113903.png?raw=true)

## 7. Rebase operation 

Suppose A makes some commits on the master branch to update, and B wants to continue working on these changes, he can use the rebase operation to update his branch.

```bash
git checkout add_lwh
git rebase main
```

If a conflict is encountered during the rebase, Git pauses the rebase and lets B resolve the conflict. After resolving the conflict, B continues the rebasing process.

```bash
git add introduction.md
git rebase --continue
```
Eventually, B can push his changes to GitHub again (forced push may need to be used since the history has been changed):

```bash
git push origin add_lwh --force
```
![This is an image](https://github.com/liyinred/Test1/blob/main/pic/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20240412135404.png?raw=true)