## Git命令
```git
git rm directoryname -r -f //删除stage 中的文件夹
git archive //打包成可以发布的压缩包
git diff // check the changes before the file was added.
git log  // --pretty=oneline check commit log 只显示一行递交日志
git reflog //最近使用的命令
git log --graph /用图形显示最近的提交状况
```
## Git须知
* de0f7af4a7b8a91aeddec1d1a11b227c0abf3546 append GPL
108236f87f8d615c50cdc68df0a4da381b8edbe5 new char
7745e97f222147e397c373f5b7be29c4fc377286 first file in git
十六进制的字符串随机生成来标记commit id
* Git必须知道当前版本是哪个版本，在Git中，用HEAD表示当前版本，上一个版本就是HEAD^，上上一个版本就是HEAD^^，当然往上100个版本写100个^比较容易数不过来，所以写成HEAD~100。

```git
git reset //回到上一个版本
git reset --hard HEAD^ //同样是回到上一个版本
git checkout -- filename //在添加之前取消修改
git checkout -- readme.txt // 
```
一种是readme.txt自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态;
一种是readme.txt已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。
总之，就是让这个文件回到最近一次git commit或git add时的状态。

```git
git reset HEAD -- filename //撤销修改
git checkout -- filename //取消工作区的修改
```
关于删除的命令
```git
git rm filename //确实要删除该文件
git commit -m " " //提交修改

git checkout -- filename //撤销修改
```
## GitHub
将本地库与GitHub连接起来
1. 创建SSHKey。在用户主目录下，看看有没有.ssh目录，如果有，再看看这个目录下有没有id_rsa和id_rsa.pub这两个文件，如果已经有了，可直接跳到下一步。如果没有，打开Shell（Windows下打开Git Bash），创建SSH Key：
```git
$ ssh-keygen -t rsa -C "youremail@example.com"
```
你需要把邮件地址换成你自己的邮件地址，然后一路回车，使用默认值即可，由于这个Key也不是用于军事目的，所以也无需设置密码。如果一切顺利的话，可以在用户主目录里找到.ssh目录，里面有id_rsa和id_rsa.pub两个文件，这两个就是SSHKey的秘钥对，id_rsa是私钥，不能泄露出去，id_rsa.pub是公钥，可以放心地告诉任何人。
2. 在github上创建一个新的仓库，将本地库与远程库连接起来。
```git
git clone URL
git push -u origin master //orgin 远程的master分支
git push orgin master // 非第一次，可以取消-u参数
```
3. 分支的创建和合并
```git
git  checkout -b  dev //create and change into the branch
git checkout master //return master match
git merge branchname //merge branchname into current branch
git branch -d dev //delete dev branch
```
4. 分支管理
```git
git stash //保存现场
git stash pop //恢复工作区并弹出断点
git stash apply //恢复工作区不弹出断点
git branch -D name //强行删除分支
```
