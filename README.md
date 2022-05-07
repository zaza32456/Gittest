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

提交后突然发现没有新增修改和提交修改，所以dev和main分支的内容是一样一样儿的,还是上次commit时的内容。

### 让我们重新将修改添加到暂存区，并commit

```
git add README.md
git commit -m"新建dev分支，并添加在README里添加一些内容"
```
commit后,Bash显示如下内容：

```
[dev ec30a64] 新建dev分支，并添加在README里添加一些内容   //此次commit后的版本号为ec30a64
 1 file changed, 34 insertions(+)   //1个文件被修改（READ.md）,新增了34行内容
```

### 再次推送，我们就能看到dev分支新增的内容辣

```
git push origin dev
```