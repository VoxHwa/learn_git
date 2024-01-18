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

