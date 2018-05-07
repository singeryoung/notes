## git使用入门 20180507

### 1.初始化git仓库

命令：`git init`

注意：创建的仓库的路径中不要包含中文

### 2.配置用户名和邮箱

- 配置全局用户名

命令`git config --global user.name '{用户名}' `

> 例如：`git config --global user.name 'yyx' `

- 配置全局电子邮箱

命令`git config --global user.email '{电子邮箱}'`

> 例如：`git config --global user.email 'yyx@gmail.com'`

- 删除全局用户名

命令`git config --global --unset user.name`

- 删除全局电子邮箱

命令`git config --global --unset user.email`

- 查看全局配置列表（可以看到是否配置了用户名和电子邮箱）

命令`git config --global --list`

### 3.文件放到git仓库

几个概念：

- 工作区（Working Directory）

- 暂存区（Stage）

- 版本库（Repository）

  > `git add`命令实际上就是把要提交的所有修改放到暂存区（Stage），然后，执行`git commit`就可以一次性把暂存区的所有修改提交到分支。

提交步骤：

1. 把文件加入到暂存区 `git add {文件路径}`
2. 将暂存区的文件提交到版本库的当前分支 `git commit -m '{提交描述信息}'`

例如：

> `git add js/common.js`
>
> `git commit -m 'update common.js'`

在仓库根目录提交所有修改的文件，`git add ./`或者`git add *`

常用情形，提交所有修改文件：

- 所有修改的文件放到暂存区
- 将暂存区的文件提交到工作区

> `git add ./`
>
> `git commit -m 'update some files'`

两步合并`git commit --all -m '{update some files}'`

### 4.忽略提交文件列表文件.gitignore

语法：`/path`以斜杠（/）开头，后面跟要忽略提交的文件路径

忽略文件一行写一个路径，多个换行书写

### 5.查看状态（是否修改，是否提交）

命令`git status`

红色的文件名：发生修改，但未被加入到暂存区的文件

绿色的文件名：被加入到暂存区，但未被提交到工作区的文件

###6.查看日志

命令`git log `列出全部提交日志

命令`git log --oneline`列出简洁版日志

命令`git log -{数字}`列出最近的指定条数的日志

> 例：`git log -3`列出最近3条的日志

###7.版本回退

命令`git reset --hard Head^`回退到上次提交的版本

命令`git reset --hard Head~1`回退到上次提交的版本，与上面等同

注意：Head~0指向当前所在的提交版本

### 8.通过版本号切换

命令`git reflog`查看所有分支的所有操作记录

命令`git reset --hard {版本号信息} `

###9.分支管理

默认一个分支——主分支master

- 创建分支

命令`git branch {分支名}`

- 切换分支

命令`git checkout {分支名}`

- 查看分支

命令`git branch`

- 合并分支

命令`git merge {分支名}`

- 删除分支

命令`git branch -d {分支名}`

### 10.把本地代码推送到服务器上

代码托管平台

- 国际：github、gitlab、bitbucket
- 国内：码云gitee、码市coding

推送方法：

- https的push到仓库方法 `git push {https仓库地址} master`
- https的pull到仓库方法 `git pull {https仓库地址} master`
- ssh的推送`git push origin master`提交本地代码到远程仓库
- ssh的推送下拉`git pull origin master`从远程仓库拉去最新代码
- `git clone {仓库名字}`从远程的仓库克隆到本地(要配置密钥)



其他命令

git diff

提交后，用`git diff HEAD -- readme.txt`命令可以查看工作区和版本库里面最新版本的区别

`git checkout -- {文件名}`可以丢弃工作区的修改



用`git log`可以查看提交历史，以便确定要回退到哪个版本。

用`git reflog`查看命令历史，以便确定要回到未来的哪个版本。



#### 