## Chapter 3

__分支Branch__

### 分支查看命令

```bash
git branch
```

```
* master
```

*表明当前处在的分支

## 分支创建命令

```bash
git branch 新分支名称
```

## 分支的删除

在Git中没有什么分支是不可以删除的（除了当前所在的分支不能删除），包括`master`分支也是可以进行删除。
Git的分支删除可以分为删除本地分支和远程分支。

- 删除本地分支

```bash
# branchName 是需要删除的本地分支名字
git branch -d branchName
```

当我们想强行删除分支时，只需要将参数d改为D即可。

- 删除远程分支

```bash
# origin 是远程的主机名
# branch 需要删除的远程分支
git push origin --delete branch
```

## 分支切换

```bash
git checkout 分支名称
```

会提示```Switched to branch xxx```	

## 分支特性

__独立分支操作__

当我们在新分支创建修改文件，我们再add并commit，__所记录的一切操作都会与其他分支独立开__。切到其他分支，新分支下的独立文件将消失。

如果我们不commit，切到其他分支，则会保留新分支文件。

以commit决定操作文件所属分支，可以在A分支add，在B分支commit一个文件，文件属于B分支。

## 分支合并

前提是必须在__主分支__上进行合并

```bash
git checkout master #回到主分支
git merge 需要合并的分支名称
```

可以使用```git branch --no-merged```查看所有未合并的分支

### 分支合并失败

- 手动合并

  手动合并的方法很简单，就是我们__选择我们要保留的代码，然后再把>>>>>, ======, <<<<<<这些提示行给去掉。最后重新进行add commit的操作即可__。

  冲突文件会变成这样子：

  ```txt
  <<<<<<< HEAD 	主分支文件冲突内容
  master and branch
  new line
  ======= 		分割线
  If u can see this file, it's on try branch now.
  U canNOT
  >>>>>>> try 	try分支文件冲突内容
  ```

- 放弃合并

  当我们发现冲突所导致的改动量很大时，我们可以选择放弃该次的合并。我们可以使用`git merge --abort`放弃此次的融合。如果我们在运行了git merge之后又进行了一些人为的改动，那么在abort之后，所进行的改动也会被回滚掉。

- mergetool

  除了手动合并以及放弃合并之外，我们还有一些其他的合并工具。git官方开发了一个专门用来合并的工具，叫做git mergetool(下图所示)，它会将找到一份两个分支的祖先代码作为base（基准），然后再将两个分支的改动都列举出来作为对比，让我们在git编辑器当中决定要留下什么。在此处，我们不做过多的阐述，感兴趣的同学可以点击下方链接进行查看。

  1. [Use vimdiff as git mergetool](https://www.rosipov.com/blog/use-vimdiff-as-git-mergetool/)
  2. [使用vimdiff作为git mergetool](https://kinboyw.github.io/2018/10/09/Use-Vimdiff-As-Git-Mergetool/)
  3. [git-mergetool](https://www.lhsz.xyz/read/git-doc-zh/docs-16.md)



## 分支工作原则

在实际开发中，我们应该按照以下几个基本原则进行分支开发工作流程

1. master分支__应该是最稳定的__，也就是__仅用来发布新版本__，*平时不能直接在上面进行操作，应该保存在远程*。
2. 短期分支是我们干活的分支，短期分支可以不用上传到远程，当我们完成了bug的修复，新功能的开发时才需要合并到主分支上。
3. __多使用分支__来进行开发工作。

