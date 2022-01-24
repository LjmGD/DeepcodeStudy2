## git操作命令

```markdown
# 列出所有本地分支
git branch
# 列出所有远程分支
git branch -r
# 新建一个分支，但依然停留在当前分支
git branch [branch-name]
# 新建一个分支，并切换到该分支
git checkout -b [branch]
# 合并指定分支到当前分支
$ git merge [branch]
# 删除分支
$ git branch -d [branch-name]
# 删除远程分支
$ git push origin --delete [branch-name]
$ git branch -dr [remote/branch]
```

1. git init //初始化
2. git remote add origin 仓库的ssh //连接到远程仓库 
3. git add . 添加所有文件
4. git add 文件名.后缀 //推送到暂存区
5. git commit -m "备注信息"//推送到本地仓库
6. git push origin 分支名称//推送到远程仓库

### git删除文件夹

1. ` git pull origin master` 将远程仓库里面的项目拉下来
2. `git rm -r --cached PrintTask` 删除 PrintTask 文件夹
3. `git commit -m '删除了PrintTask'` 提交添加操作说明。
4. ` git push -u origin master` 将本次更改更新到github项目上去，删除完毕。

