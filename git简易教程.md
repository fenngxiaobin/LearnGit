#git简易教程

git相比于svn优点，离线可用，创建分支简单，不依赖服务器

1.创建新git仓库

打开新文件夹，执行

```git
git init
```

检出仓库

执行以下命令，

```git
git clone https://github.com/xxxxxx/xxx.git
```

创建一个远程仓库的克隆版本。

2.查看文件状态

```git
git status
```

3.提交到仓库

```git
git status
```

4.提交信息

```git
git commit -m '备注'
```

5.查看所有commit记录
```git
git log
```
理解git仓库的概念：

一个本地仓库由三个区域构成，每个区域理解为树结构。第一个区域为实际的文件树结构（工作目录），第二个区域为暂存区，是一个缓存区，保存add命令添加的文件，第三个区域是HEAD，指向最后一次提交的结果。

![](/home/fengxb/Desktop/git stage.png)

添加和提交：

第一步，将修改的文件添加到暂存区，

```git
git add <filename> 或者
git add *
```

第二步，将改动提交

```git
git commit -m "备注信息"
```

每一次提交会根据SHA算法分配一个唯一ID（比如1d2e4r2e2wwff...），为了方便记忆

可以创建一个标签：

```git
git tag v.1.0.0 1d2e4r2e2ww
```

使用 `git log`命令查看



推送改动到远程仓库

```git
git push origin master
```

master可以替换为本地任何分支，比如 git push origin branch1

如果没有将本地仓库连接到远程服务器，可以使用如下命令：

```git
git remote add origin git@github.com:username/project_name.git
```

 接下来可以将你的后续改动推送到服务器上去。

分支的概念，

分支是用来做新功能开发时使用的，master分支是默认的主分支，不建议直接修改，一个在其他分支上做开发，完成后将分支合并到master分支。![深度截图_选择区域_20180802234524](/home/fengxb/Desktop/深度截图_选择区域_20180802234524.png)

创建一个feature_x分支，并切换到该分支。

```git
git checkout -b feature_x
```

切换回主分支

```git
git checkout master
```

删除新建分支：

```git
git branch -d feature_x
```

除非你将分支推送到远端仓库，不然该分支就是 *不为他人所见的*：

```git
git push origin feature_x
```

合并分支，

```git
git merge <branch>
```

如果我当前在master分支，git merge feature_1   就是将feature_1分支合并到master分支。不是每次合并都会成功，如果出现冲突可以先预览分支差异：

```git
git diff <source_branch> <target_branch>
```

手动合并文件，然后

```git
git add <files>
```

查看仓库提交历史：

```git
git log
```

调整日志输出的手段，

比如查看某个人的提交`git log --author=fxb `

简化日志输出 `git log --pretty=oneline`

以图的形式输出：`git log --graph --oneline --all`

操作撤销

1.如果你想撤销对文件修改或者是误删除，且这些文件没有add进缓冲区，可以使用

```git
git checkout -- filename
```

该操作会用HEAD中的最新内容来替换工作区的内容。

2.如果你已经将文件add进缓冲区，但没有commit

```git
git reset HEAD <filename>
```

3.如果文件已经commit，那么可以回滚到上一个版本

```git
git reset --hard commit_id （返回到指定commit_id的版本）
git reset --hard HEAD^ (返回上一个版本)
```



如有疑问使用

```git
git help key_word
```



