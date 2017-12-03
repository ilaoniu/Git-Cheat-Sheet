# Git 常用操作命令

### 目录
* [配置](#配置)
* [创建](#创建)
* [本地修改](#本地修改)
* [搜索](#搜索)
* [提交历史](#提交历史)
* [分支与标签](#分支与标签)
* [更新与发布](#更新与发布)
* [合并](#合并)
* [撤销](#撤销)

## 配置

##### 设置用户名：
```
$ git config --global user.name “[firstname lastname]”
```

##### 设置邮箱地址：
```
$ git config --global user.email “[valid-email]”
```

##### 设置命令行显示为更易阅读的彩色：
```
$ git config --global color.ui auto
```

## 创建

##### 克隆一个已存在的分支：


通过 SSH

```
$ git clone ssh://user@domain.com/repo.git
```

通过 HTTP

```
$ git clone http://domain.com/user/repo.git
```

##### 创建一个新的本地分支：
```
$ git init
```

## 本地修改

##### 显示工作路径下文件状态：
```
$ git status
```

##### 显示已追踪文件的修改：
```
$ git diff
```

##### 把当前所有修改添加到下次提交中：
```
$ git add .
```

##### 把对某个文件的修改添加到下次提交中：
```
$ git add <file>
```

##### 提交本地所有已追踪文件的修改：
```
$ git commit -a
```

##### 带上说明提交更改：
```
$ git commit -m 'message here'
```

##### 修改上次提交：
<em><sub>不要修改已发布的提交记录！</sub></em>

```
$ git commit -a --amend
```

##### 把当前分支中未提交的修改暂存，并带到其他分支：
```
$ git stash
$ git checkout branch2
$ git stash pop
```

##### 将最近一次暂存的工作进度恢复到当前分支：
```
$ git stash apply
```

#### 将暂存的某个工作进度恢复到当前分支：
- *{stash_number}* 可以用以下命令 `git stash list` 获取

```
$ git stash apply stash@{stash_number}
```

##### 删除最近一次暂存的工作进度：
```
$ git stash drop
```

## 搜索

##### 从当前目录的所有文件中查找文本内容：
```
$ git grep "Hello"
```

##### 在某个版本中搜索文本内容：
```
$ git grep "Hello" v2.5
```

## 提交历史

##### 从最新提交开始，显示所有提交记录：
```
$ git log
```

##### 显示所有提交记录简要信息：
```
$ git log --oneline
```

##### 显示某个用户的所有提交：
```
$ git log --author="username"
```

##### 显示某个文件的所有修改：
```
$ git log -p <file>
```

##### 谁，在什么时候，修改了文件的什么内容：
```
$ git blame <file>
```

##### 显示所有操作记录：
```
$ git reflog
```

##### 删除所有操作记录：
```
$ git reflog delete
```

## 分支与标签

##### 列出所有本地分支：
```
$ git branch
```

#### 列出所有本地/远程分支：
```
$ git branch -a
```

##### 列出所有远程分支：
```
$ git branch -r
```

##### 切换当前分支：
```
$ git checkout <branch>
```

##### 从不同分支中检出某文件：
```
$ git checkout <branch> -- <filename>
```

##### 创建并切换到新分支：
```
$ git checkout -b <branch>
```

#### 基于一个已存在的提交创建并检出一个新分支：
```
$ git checkout <commit-hash> -b <new_branch_name>
```

##### 基于当前分支创建一个新分支：
```
$ git branch <new-branch>
```

##### 基于远程分支创建新的可追溯的分支：
```
$ git branch --track <new-branch> <remote-branch>
```

##### 删除本地分支：
```
$ git branch -d <branch>
```

##### 重命名当前分支：
```
$ git branch -m <new_branch_name>
```

##### 强制删除本地分支：
<em><sub>将会丢失未合并的修改！</sub></em>

```
$ git branch -D <branch>
```

##### 给当前版本打标签：
```
$ git tag <tag-name>
```

##### 给当前版本打标签并附带说明：
```
$ git tag -a <tag-name> -m 'message here'
```

## 更新与发布

##### 列出当前配置的远程仓库：
```
$ git remote -v
```

##### 显示远程仓库的信息：
```
$ git remote show <remote>
```

##### 添加新的远程仓库：
```
$ git remote add <remote> <url>
```

##### 拉取远程端修改内容，但不合并到当前分支：
```
$ git fetch <remote>
```

##### 拉取远程端修改内容，并自动合并到当前分支：
```
$ git remote pull <remote> <url>
```

##### 拉取远程端修改内容，并自动合并到当前分支：
```
$ git pull origin master
```

##### 拉取远程端修改内容，并变基到当前分支：
```
$ git pull --rebase <remote> <branch>
```

##### 将本地版本发布到远程端：
```
$ git push remote <remote> <branch>
```

##### 删除远程端分支：
```
$ git push <remote> --delete <branch>
```

##### 发布标签：
```
$ git push --tags
```

## 合并

##### 将指定分支合并到当前分支：
```
$ git merge <branch>
```

##### 手动解决冲突后，将文件标记为“已解决冲突”：
```
$ git add <resolved-file>
```

```
$ git rm <resolved-file>
```

## 撤销

##### 放弃工作目录下的所有修改：
```
$ git reset --hard HEAD
```

##### 移除暂存区的所有文件(即撤销之前的 `git add`)：
```
$ git reset HEAD
```

##### 放弃某个文件的所有本地修改：
```
$ git checkout HEAD <file>
```

##### 回到上次提交之前(通过新建一个与之相反的提交)：
```
$ git revert <commit>
```

##### 将 HEAD 重置到之前的某个版本，并丢弃之后的所有修改：
```
$ git reset --hard <commit>
```

##### 将 HEAD 重置到远程分支：
```
$ git reset --hard <remote/branch> e.g., upstream/master, origin/my-feature
```

##### 将 HEAD 重置到之前的某个版本，并保留所有未暂存的修改：
```
$ git reset <commit>
```

##### 将 HEAD 重置到之前的某个版本，并保留未提交的本地修改：
```
$ git reset --keep <commit>
```

##### 删除添加 `.gitignore` 之前错误提交的文件：
```
$ git rm -r --cached .
$ git add .
$ git commit -m "remove xyz file"
```
