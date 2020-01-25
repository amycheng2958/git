# [git入门](https://www.liaoxuefeng.com/wiki/896043488029600)

> `来源慕课网git入门----byTyler`

## git仓库

* 初始化版本库：`git init`
* 添加文件到版本库：`git add` ;  `git commit`
* 查看仓库状态： `git status`
* 回滚暂存区的文件(git add后的文件)：`git reset HEAD <filename>`; `git checkout -- <filename>`
* 回滚本地仓库的文件(一般不建议)： 先查看commit号`git log(--pretty=oneline)`; `git reset --hard <commit id>`
* 删除本地仓库文件：`git rm <filename>`; `git commit -m 'delete'`

## 远程仓库
* 配置邮箱：git config [--local|--global|--system]（--replace-all) user.email "790958649@qq.com"
* 配置用户名：git config [--local|--global|--system]（--replace-all) user.name
* 删除配置：git config [--local|--global|--system] --unset section.key
* 生成SSH key：`ssh-keygen -t rsa -C "github邮箱"`,生成后的公钥在目录`~/.ssh`中的`id_rsa.pub`,复制后黏贴到github中`settings`中`SSH`,通过`ssh -T git@github.com`测试是否连通
* 添加远程仓库: `git remote add origin <地址>`，远程库的名字就是origin；`git pull origin master，--allow-unrelated-histories`，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令;`git push -u origin master` 
* 删除远程仓库：`git remote rm origin`
  
## 标签管理

* 查看所有标签 `git tag`
* 创建标签 `git tag <name>`
* 指定提交信息 `git tag -a <name> -m "comment"`
* 删除标签 `git tag -d <name>`
* 标签发布 `git push origin <name>` 

## 分支管理

* 添加分支：`git branch <branchname>`,添加分支后切换到新分支，需要先commit，将新分支添加到远程仓库`git push --set-upstream origin`
* 查看当前分支：`git branch`
* 切换分支：`git checkout <branchname>`
* 合并分支：`git checkout master`;`git merge <branchname>`
* 删除分支：`git branch -d <branchname>`

## 总结

* **如何撤销修改？**
* `场景1`：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令`git checkout -- <file>`
  
* `场景2`：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令g`it reset HEAD <filename>`，就回到了场景1，第二步按场景1操作。

* `场景3`：已经提交了不合适的修改到版本库时，想要撤销本次提交，使用版本回退,用命令`git log`查看commit id，然后使用 `git reset --hard commit_id` 回退到指定版本,不过前提是没有推送到远程库。要重返未来，用git reflog查看命令历史，以便确定要回到未来的哪个版本  

* **分支操作**
* 查看分支：git branch
* 创建分支：git branch <name>
* 切换分支：git checkout <name>或者git switch <name>
* 创建+切换分支：git checkout -b <name>或者git switch -c <name>
* 合并某分支到当前分支：git merge <name>
* 删除分支：git branch -d <name>
