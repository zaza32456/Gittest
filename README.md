# Gittest

## main 
刚刚clone了空的仓库，现在修改一下readme，再提交一次。

### 提交前先将更改保存到暂存区

``` 
git add README.md
```

### 并提交

```
git commit -m"克隆仓库后修改readme并推送"
```

### 推送到远程仓库。（clone会在本地仓库和远程仓库间建立链接。）

```
git push -u origin main
```

## main

### 在github上修改了README，重新将最新的版本pull到本地仓库，使本地仓库和远程仓库内容同步

```
git pull
```

此时新拉取的内容直接合并到了main中。

### 现在新建一个分支dev，在上面继续对README的内容进行修改。

```
git switch -c dev 
```

或者使用

```
git checkout -b dev
```

### 现在我们提交到dev分支上

```
git push origin dev
```

## dev 

提交后突然发现dev和main分支的内容是一样一样儿的,因为没有新增修改和提交修改，所以还是上次commit时的内容。

### 让我们重新将修改添加到暂存区，并commit

```
git add README.md
git commit -m"新建dev分支，并添加在README里添加一些内容"
```
commit后,Bash显示如下内容：

```
[dev ec30a64] 新建dev分支，并添加在README里添加一些内容   //此次commit的版本号为ec30a64（这里打错字了，多了一个添加）
 1 file changed, 34 insertions(+)   //1个文件被修改（READ.md）,新增了34行内容
```

### 再次推送，我们就能看到dev分支新增的内容辣

```
git push origin dev
```

## main

刚才我发现，有一些文字描述有点小错误，于是我修改了一下，add并commit。

现在我又在README.md里增加了对上述操作的说明，然后打算把dev上的内容合并大main里。

### 让我们切换回main分支，现在我们要把dev分支的内容合并到main
```
git switch main   //或 git checkout main
```

此时Bash没有转换分支，反而是给我报了个错误：

```
error: Your local changes to the following files would be overwritten by checkout:
        README.md
Please commit your changes or stash them before you switch branches.
Aborting
```
### 报错内容告诉我，我在切换分支前需要commit或者stash，否则会丢失我目前的所有修改。
这是因为我在coommit后才又在README.md里加了几行字（line75~81），于是我现在打完这句话后会重新add,commit并push,这样就能保证我的修改完整提交到dev并清空工作区，为main分支为下一步的合并做准备。

## main

```
$ git merge dev
Updating e2206bf..fece9c2
Fast-forward
 README.md | 73 +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
 1 file changed, 73 insertions(+)

```

### 在执行命令 git merge dev后，我竹汉三又回来啦！

现在main和dev上的内容已经完全一致了，dev已经完成了他的使命，可以光荣退休了。

在删除dev之前，让我们吸取之前的教训，随时记得commit或stash，就像我们玩galgame一样，在面临一个选择前永远要记得给自己留个后路。

```
$ git add README.md

$ git commit -m"准备删除dev分支"
[main XXXXXXX] 准备删除dev分支    //XXXXXXX是此次commit版本号
 1 file changed, 18 insertions(+)
```