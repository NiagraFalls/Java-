# Git简介
安装Git
创建版本库
# 时光机穿梭
# 远程仓库
Git杀手级功能之一：远程仓库
Git作为分布式版本控制系统，各个克隆库没有主次之分

Git服务器：
1.自己搭建服务器
2.用Github提供Git仓库托管

SSH:Secure Shell,TCP外面套了一层。Github支持Git协议和HTTPS协议。Git协议基于SSH开发。

SSH使用RSA密码学算法，生产公钥和私钥。公钥添加在Github网站，私钥放在自己本地，是一个非常长的字符串。用于匹配服务器，让Github知道你push的commit确实是你push的。

Github可以添加多个key,用于多个电脑进行开发。

Github上的公开库所以人都可见，但是只有自己可以修改。私有库别人看不见。

PUSH/PULL
## 添加远程库
把本地的仓库同步到远程仓库，作为备份，别人也可以通过远程库来进行分布式协作。

在Github创建空仓库，注意和本地仓库要同名

在Gitbash输入 git remote add origin git@github.com:y用户名/仓库名

git push -u origin master
-u是初次推送master用来连接的，后面就不需要了

GIT开发过程：本地创作->add 暂存区->commit到HEAD->push到远程git push orgin master

> "分布式版本系统的最大好处之一是在本地工作完全不需要考虑远程库的存在，也就是有没有联网都可以正常工作，而SVN在没有联网的时候是拒绝干活的！当有网络的时候，再把本地提交推送一下就完成了同步，真是太方便了！"

> ---Liao Xuefeng
## 从远程库克隆

一般，都是先创建远程库，然后从远程库克隆开发，使用git clone命令

支持SSH和HTTPS(我已经把HTTPS进行了优化，下载速度提升)。
问题是每次推送都要输入口令。

这个问题已经解决：重新生成钥匙对，过程中不要输入自己的账户密码，就可以使用GIT协议进行clone
# 分支管理
Git分支的创建和切换非常快，相比于SVN
## 创建与合并分支
### 创建分支
`git checkout -b dev`
-b表示创建并切换到新建分支
；`git switch -c dev`

`git branch`查看当前分支；列出所有分支，当前分支前面有星号

`git checkout master`; `git switch master`都可以用来切换分支
### 合并分支
`git merge dev`合并分支

`git branch -d dev`删除分支
## 解决冲突
合并分支遇到这个问题
```
CONFLICT (content): Merge conflict in readme.txt
Automatic merge failed; fix conflicts and then commit the result.
```
用`git status`发现冲突事件。表明合并冲突，需要手动把文件修改成你希望的模式，然后提交就可以。最后记得把多余分支删除掉。

`git log --graph --pretty=oneline --abbrev-commit`查看分支合并的图示
## 分支管理策略
合并分支默认使用fast-forward模式，缺点：删除分支后，会丢掉分支信息。

`git merge --no-ff -m "merge with noff" dev`可以强制禁用ff模式合并，保留分支信息

master分支异常稳定，仅用来发布新版本，不能再上面干活

dev分支用来干活，是不稳定的

每个人都在dev分支干活，所以每个人都有自己的分支，到时候往dev分支进行merge就行

## Bug分支
修bug用的临时分支，完成后应该删除
## Feature分支
开发新功能用的临时分支，完成后应该删除

`git stash`用来保存现场

`git stash list`查看工作现场保存栈

恢复现场的方法：1.`git stash pop`恢复顶部并删除顶部现场2.`git stash apply`+`git stash drop `

恢复指定现场用`git stash apply stash@{0}`+`git stash drop stash@{0}`
## 多人协作
## Rebase