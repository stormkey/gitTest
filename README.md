# Git

> git常用指令

#### Git指令

``` bash

# 切换目录文件
  在进行任何Git操作之前，都要先切换到Git仓库目录。也就是切换到项目的文件目录下。

# 查看项目状态
  git status -> 查看状态，这个命令可以算是使用最频繁的一个命令了，建议大家没事就输入下这个命令，来查看你当前 git 仓库的一些状态。

# 项目初始化
  git init -> 项目初始化，使当前项目成为一个Git仓库

# 新建文件添加到[暂存区]
  git add 文件名 -> 新建文件夹或文件都还没有提交到git仓库。
  
# 新建文件或文件夹提交和注释
  git commit -m "提交说明注释" -> commit 是提交, -m 是要提交的信息, ""里的内容是提交时的注释
 
# push文件到master主分支
  git push 仓库名称 master -> git commit提交后并没有在master及时更新。需要push 后刷新后才能看到
  
# 查看上一次提交修改的内容
  git diff 文件名.后缀 -> 如果忘记上次提交了什么内容，可以通过此命令查看
 
# 查看提交记录
  git log -> 查看所有 commit 记录,如果嫌信息太多,可以在后面添加参数 git log --pretty=oneline
  
# 查看所有分支
  git branch ->  默认分支为主分支 master
 
# 创建新分支
  git branch 分支名称 -> 创建新分git 支
  
# 切换分支
  git checkout 分支名称 -> 切换提交的分支
  
# 创建新分支并切换到新分支
  git checkout -b 分支名称 -> 创建新分支并切换到新分支

# 删除分支
  git branch -d 分支名称 -> 删除分支
  git branch -D 分支名称 -> 强制删除分支
  
# 合并分支
  git merge 分支名称 -> 合并分支前先切换到master分支 然后在执行 git merge 分支名称
  git merge --no-ff -m "提交注释" dev -> 合并分支时，加上--no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而fast forward合并就看不出来曾经做过合并。
  
# 分支合并情况
  git log --graph --pretty=oneline --abbrev-commit
  
# 创建新分支并同步远程仓库
  git checkout -b dev -> 创建并切换到新分支
  git push origin HEAd -u -> 将新分支同步到github上
  
# 删除新分支并同步远程仓库
  git branch -d dev -> 删除创建的分支
  git push origin :dev -> 删除分支后同步github， origin 可以为仓库名称。(:)冒号后面为要删除的分支名称
  
# 其他开发人员从远程仓库克隆项目代码
  git clone git@github.com:stormkey/gitTest.git -> 如果是在另外一台电脑则需要吧SSH Key添加到Github，克隆下来后只能看到本地的master分支
  
# 创建本地dev分支
  git checkout -b dev origin/dev  
  
# 本地dev分支与远程仓库origin/dev做链接
  git branch --set-upstream-to=origin/dev dev

# 查看历史版本
  git reset --hard HEAD^ -> 上上个版本就是 HEAD^^ 假如上100个版本 -> HEAD~100

# 指定回到某个版本
  git reset --hard 版本号前五位及以上 -> 指定回到某个修改之前的版本，可通过git log 查看版本号

# 历史命令
  git reflog -> 查看历史命令

# 提交项目前确认自己用户名及邮箱地址
  git config user.name -> 查看当前用户名
  git config user.email -> 查看当前邮箱地址
  
# 修改用户名和邮箱地址
  git config --global user.name "newName" -> 引号中写要修改的用户名
  git config --global user.email "newEmail" -> 引号中写要修改的邮箱地址
  
# 查看配置信息
  git config --list -> 查看所有配置文件信息
  
# 查看文件内容
  cat 文件名.后缀 -> 查看文件的内容
  
# 删除文件
  git rm 文件名称 -> 删除不需要的文件，误删也可恢复

```

> 估计很多人会有疑问，我想要提交直接进行 commit 不就行了么，为什么先要再 add 一次呢？
> 首先 git add 是先把改动添加到一个「暂存区」，你可以理解成是一个缓存区域，临时保存你的改动，
> 而 git commit 才是最后真正的提交。这样做的好处就是防止误提交，当然也有办法把这两步合并成一步。  
> 不过后面再介绍，建议新手先按部就班的一步步来。。。

> 当你要删除文件的时候，可以采用命令：rm test.txt
> 这个时候（也就是说这个时候只执行了rm test.txt）有两种情况
> 第一种情况:的确要把test.txt删掉，那么可以执行
> - git rm test.txt
> - git commit -m "remove test.txt"
> - 然后文件就被删掉了

> 第二种情况删错文件了，不应该删test.txt，注意这时只执行了rm test.txt，还没有提交，所以可以执行git checkout test.txt将文件恢复。
> 并不是说执行完git commit -m "remove test.txt"后还能用checkout恢复，commit之后版本库里的文件也没了，自然没办法用checkout恢复，而是要用其他的办法

团队多人协作工作模式参考：[多人协作工作模式](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013760174128707b935b0be6fc4fc6ace66c4f15618f8d000/ "多人协作")<br/>
有关如何学习Git：[廖雪峰的官方网站](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/ "廖雪峰的官方网站")<br/>
如有什么建议或者意见请发送至我的邮箱：[vaeyang1001@gmail.com] 一起学习探讨
