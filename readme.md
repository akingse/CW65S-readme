# Github

原使用环境，神舟战神k650笔记本，Ubuntu16.04，ros kinetic;

```shell
akingse@cw65s-ubuntu
lsb_release -a
```

> Distributor ID:	Ubuntu
> Description:	Ubuntu 16.04.7 LTS
> Release:	16.04
> Codename:	xenial

## ROS_workspace

> ros_catkin_ws
>
> /home/akingse/catkin_ws
>
> ros_tutorial_ws
>
> /home/akingse/tutorial_ws
>
> ros_package_ws
>
> /home/akingse/package_ws
>
> ros_project_ws
>
> /home/akingse/下载/project_ws
>

可使用vscode插件同步，更加便捷；

---

```help
These are common Git commands used in various situations:

start a working area (see also: git help tutorial)
   clone      Clone a repository into a new directory
   init       Create an empty Git repository or reinitialize an existing one

work on the current change (see also: git help everyday)
   add        Add file contents to the index
   mv         Move or rename a file, a directory, or a symlink
   reset      Reset current HEAD to the specified state
   rm         Remove files from the working tree and from the index

examine the history and state (see also: git help revisions)
   bisect     Use binary search to find the commit that introduced a bug
   grep       Print lines matching a pattern
   log        Show commit logs
   show       Show various types of objects
   status     Show the working tree status

grow, mark and tweak your common history
   branch     List, create, or delete branches
   checkout   Switch branches or restore working tree files
   commit     Record changes to the repository
   diff       Show changes between commits, commit and working tree, etc
   merge      Join two or more development histories together
   rebase     Forward-port local commits to the updated upstream head
   tag        Create, list, delete or verify a tag object signed with GPG

collaborate (see also: git help workflows)
   fetch      Download objects and refs from another repository
   pull       Fetch from and integrate with another repository or a local branch
   push       Update remote refs along with associated objects
```





```shell
git config --global user.name "akingse"
git config --global user.email "akingse@qq.com"
ssh-keygen -t rsa -C "akingse"


```

```
The key fingerprint is:
SHA256:0xB6LTWGdfQmgrHYPv1mjCUdqJeF+Ef6/xnlG7WkkUI akingse
cat /home/akingse/.ssh/id_rsa.pub
ssh-rsa AAAAB3N......

ssh -T git@github.com
```

### [教程 SSH keys配置](https://blog.csdn.net/qq_36667170/article/details/79094257)

### [上传本地文件](https://blog.csdn.net/qwe122343/article/details/103837919)

```shell
git init
git add .
git commit -m "first commit"

git remote add origin git@github.com:akingse/ros_catkin_ws.git
git remote add origin git@github.com:akingse/ros_tutorial_ws.git
git remote add origin git@github.com:akingse/ros_package_ws.git
git remote add origin git@github.com:akingse/ros_project_ws.git

git pull --rebase origin main
git push -u origin main

git branch -m master main
git push origin main

```



```
git@github.com:akingse/CW65S-readme.git

git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:akingse/CW65S-readme.git
git push -u origin main
```



