#攻略


## level 1

初始化一个仓库

git init

## level 2

设置git的用户名和电子邮箱

git config --global user.name "ljq"

git config --global user.email "ljq@qq.com"

## level 3

将一个README文件添加到缓存区

git add README

## level 4

将缓存区的文件提交

git commit -m

## level 5

克隆远程代码库

git clone url

## level 6

克隆远程代码库到指定文件夹

git clone url folder

## level 7

忽视指定扩展名的文件提交到版本库

编辑.gitignore文件添加相关的*.扩展名的行

## level 8

忽略指定扩展名,保留该扩展名的某一文件

编辑.gitignore文件 

*.扩展名

!文件名


## level 11

一个文件被从工作区中删去了,但是没有从暂存区中删去.

找出他并删除

git rm 文件名

## level 12

一个文件被偶然地添加到了暂存区,请从暂存区删掉它,但是不要从文件系统中删除.

git rm --cached 文件名

## level 15

你添加了几个文件到仓库中,但是你需要重新规划项目结构.创建一个src文件夹,将所有.html文件移入到文件夹中.

mkdir src

git mv *.html ./src

git mv命令对暂存区中的文件进行处理.


## level 18

本地仓库中有一些标签没有推送到远程仓库中,把他们推送到远程仓库中.

在默认的情况下标签是不会被git push 命令推送到远程服务器的,也就是说,你在本地打的标签,如果没有可以执行把它推送到服务器,别人是看不到的.

把标签推送到服务器的命令如下

git push --tags

## level 21

我们有两个文件需要提交,本来打算分成两个文件进行提交,但是意外地被一同add了.现在将其中一个文件取消add.

git reset HEAD to_commit_second.rb


## level 22

你仓促地提交了代码,现在想取消最后一次提交,同事保持暂存区不变

git reset --soft HEAD^



## level 26

你需要从origin仓库更新代码

当有多人合作一起开发一个项目时,就不止时一个人向远程仓库提交代码了,你的伙伴也会向远程仓库提交代码.为了得到远程仓库的最新内容,要用下面的命了把内容抓下来.

git pull remote-name branch-name

其中,remote-name是远程仓库的名字,branch-name是远程仓库分支的名字,如果是主干那就是主干.该命令执行之后,远程仓库的代码会自动合并到本地项目中


## level 28

你本地仓库的代码是由远程仓库的origin/master分支创建的,rebase你的更新到origin/master,然后提交到远程仓库.

当你和其他伙伴一起开发时,你们都从远程仓库把文件clone到本地,然后分头开发,在分头推送到远程仓库中,推送命令如下

```shell

git push remote-name branch-name

git push -u remote-name branch-name

git push

```

第1条命令是把本地的文件推送到远程仓库，remote-name是远程仓库名，branch-name是分支名，如果你没有重命名过它们，那它们默认的名称分别是 origin 和 master；第2条命令加了一个 -u 参数，目的是让 Git 把 remote-name 和 branch-name 记住，下次就不用再写这2个参数了；第3条命令就是使用过 -u 参数以后的推送命令，不需要任何参数了。

如果别人在你之前对commit到了远程分支,当你在commit时会收到"non-fast forward"的提示,直译就是"不能快进".

有两个方法解决上述问题:

1. 使用git pull命令把远程仓库的最新代码合并到本地,然后再提交 push.**这时本地的提交和远程的提交按时间顺序混合排列.**
2. 使用git rebase,再用git push 命令把本地仓库更新排到远程仓库更新之后,那这时候本地仓库的所有提交都排在远程仓库的最后一次提交之后.


## level 30

当系统出错需要定位出错代码来源时,也就是是谁引入了错误.Git记录了详细的更新日志,通过git提供的一个专门的命令就可以定位开发者.

git blame file-name

在结果中会列出指定文件的所有代码,每行代码的左侧会列出它最后一次更新时的HASH值,开发者和时间,通过这些信息,你就可以分析每一行代码被谁编辑过了.


## level 33

你要在1.2版本中修改一个bug,切换到tag v1.2

tag是一个有语义的标签,便于记忆,我们可以把版本号或其他有特定含义的词语作为tag.当我们要切换到指定tag时,可以采用以下命令.

git checkout tag-name

## level 34

你从现在需要在app的v1.2版本上修复一个bug,切换到v1.2版本(注意有一同名分支名也为1.2)

如果存在一个和分支同名的tag,比如都叫'v1.2',那么当执行git checkout v1.2命令时,是切换到分支上,还是该切换到tag上呢?答案是切换到分支上.

如果要切换到tag,就需要按下面这样给出明确的说明:

git checkout tags/v1.2

## level 35

你忘记了在上一个提交之前创建一个分支就提交了.创建一个分支test_branch在最后一次提交之前.

默认情况下,你使用git branch branch-name语句创建分支时,创建出的分支与当前主线内容是一样的,但是你也可以指定以主线的某一次提交为基础创建分支,命令格式如下:

git branch branch-name hash-code

## level 36

你当前在本地的一个分支上做了修改,并想分享这个修改,但是并没有准备合并到master分支上.仅将test_branch分支提交到远程仓库.


由上文可知

git push remote-name branch-name

因此可以使用命令

git push origin test_branch

## level 39

在远程仓库有一个新的分支,在本地获得该分支,但不合并.

在第26关,我们曾用git pull把远程仓库的更新拉到本地仓库,这个命令其实隐含了2个连续的动作即:

1. git fetch
2. git merge

如果只住区数据并不合并,那就不能用git pull,而只用前一个动作,git fetch就可以了.

git fetch

git branch -r

git log remote-name/branch-name

第一条语句是把远程仓库的数据抓取到本地,但并不合并到本地分支;

第二条语句是查看远程分支列表,如果远程仓库有了新分支,在使用git fetch之后用 git branch -r 查看时就会发现新分支的名称,在本关中新分支的名称为'new_branch

第三条语句用于查看远程分支的日志,比插卡本地日志的git log语句多了远程仓库名和远程分支这两个参数.


## level 41

你从 wrong_branch 分支创建了一个名为 readme-update 的分支，在此分支上做了几次提交，突然你意识到你不应该从 wrong_branch 创建分支，而应该从 master 创建分支。现在你需要把 readme-update 上做过的提交迁移到 master 分支上。

git rebae --onto 参数 

## level 42

对你的仓库进行打包,确保冗余的packs已经被移除

git repack -d

## level 43

你在新功能上的努力白废了，准备删除掉它，但是往 'README' 文件里填充内容的那次提交还有用，你要把这次提交合并到主线上。


如果你创建了一个分支，在其中进行了多次提交，而在合并时不想把分支上所有的提交都合并到主线，只想选取其中的1个提交合并到主线，那么你可以用下面的命令：

git cherry-pick HASH_CODE

该功能可以是进行合并的操作.


## level 47

将分支long-feature-branch上的所有提交当做一个分支合并到主分支上.


在level 38关我们学习到merge合并.其语法是:

git merge branch-name

如果分支曾经提交过多次,那么用上面的语句合并之后,主干的日志也会出现多次提交记录.为了符合本关题意.把分支的多次提交合并为竹竿上的一次提交,要加一个squash参数,如下:

git merge branch-name --squash

如果不加squash参数,在合并之后系统会默默地做一个commit参数,而加了squash参数之后,不会自动commit,这时你还需要手动执行commit命令,并且写上提交说明.


## level 49

A bug was introduced somewhere along the way. You know that running "ruby prog.rb 5" should output 15. You can also run "make test". What are the first 7 chars of the hash of the commit that introduced the bug.

在开发过程中引入了一个 bug。已知运行 "ruby prog.rb 5" 应该输入 15，你也可以运行 "make test" 进行测试。你需要确定引入 bug 的那次提交的哈希值的前7位。

在程序持续迭代的过程中不免会引入 bug，除了定位 bug 的代码片断，我们还想知道 bug 是在什么时间被引入的，这时就可以借助 Git 提供的 bisect 工具来查找是哪次提交引入了 bug。bisect 是用二分法来查找的，就像用二分查找法查找数组元素那样。

运行 make test 可以测试程序是否正确执行，它会先执行 "ruby prog.rb 5" 语句，然后再分析输出结果是否等于15，如果不等于15，就会显示 make: *** [test] Error 1。

我们先看一下提交历史，一共20次提交：
``` 
$ git log --pretty=oneline
12628f463f4c722695bf0e9d603c9411287885db Another Commit
979576184c5ec9667cf7593cf550c420378e960f Another Commit
028763b396121e035f672ef5af75d2dcb1cc8146 Another Commit
888386c77c957dc52f3113f2483663e3132559d4 Another Commit
bb736ddd9b83d6296d23444a2ab3b0d2fa6dfb81 Another Commit
18ed2ac1522a014412d4303ce7c8db39becab076 Another Commit
5db7a7cb90e745e2c9dbdd84810ccc7d91d92e72 Another Commit
7c03a99ba384572c216769f0273b5baf3ba83694 Another Commit
9f54462abbb991b167532929b34118113aa6c52e Another Commit
5d1eb75377072c5c6e5a1b0ac4159181ecc4edff Another Commit
fdbfc0d403e5ac0b2659cbfa2cbb061fcca0dc2a Another Commit
a530e7ed25173d0800cfe33cc8915e5929209b8e Another Commit
ccddb96f824a0e929f5fecf55c0f4479552246f3 Another Commit
2e1735d5bef6db0f3e325051a179af280f05573a Another Commit
ffb097e3edfa828afa565eeceee6b506b3f2a131 Another Commit
e060c0d789288fda946f91254672295230b2de9d Another Commit
49774ea84ae3723cc4fac75521435cc04d56b657 Another Commit
8c992afff5e16c97f4ef82d58671a3403d734086 Another Commit
80a9b3d94237f982b6c9052e6d56b930f18a4ef5 Another Commit
f608824888b83bbedc1f658be7496ffea467a8fb First commit
```

首先启动 bisect 查找流程：
```
$ git bisect start
$ git bisect good f608824888b
$ git bisect bad 12628f463f4
Bisecting: 9 revisions left to test after this (roughly 3 steps)
[fdbfc0d403e5ac0b2659cbfa2cbb061fcca0dc2a] Another Commit
```
第2行和第3行是定义 bisect 的查找范围，git bisect good 和 git bisect bad 表示当前程序通过或没有通过测试，在第2行后面以第一次提交的哈希值为参数，在第3行后面以最后一次提交的哈希值为参数，说明查找范围是全部20次提交。接着 Git 定位了位于中间那个提交，它的哈希值是 "fdbfc0d403e5a"，并计算出剩余的提交还有9次，大约还需要3次二分查找。

这时，我们对程序进行测试，测试通过，所以我们反馈 good：
```
$ make test
ruby prog.rb 5 | ruby test.rb
$ git bisect good
Bisecting: 4 revisions left to test after this (roughly 2 steps)
[18ed2ac1522a014412d4303ce7c8db39becab076] Another Commit
Git 继续进行二分查找，这次定位的哈希值是 "18ed2ac1522a01"，我们再对程序测试，测试没有通过，所以我们反馈 bad：
```
$ make test
ruby prog.rb 5 | ruby test.rb
make: *** [test] Error 1
$ git bisect bad
Bisecting: 2 revisions left to test after this (roughly 1 step)
[9f54462abbb991b167532929b34118113aa6c52e] Another Commit
就这样，经过几轮测试，当 Git 给出下面的消息时，表示找到了：


18ed2ac1522a014412d4303ce7c8db39becab076 is the first bad commit


下面是对查找过程的回顾：


```


12628f463f4c72 Another Commit
979576184c5ec9 Another Commit
028763b396121e Another Commit
888386c77c957d Another Commit
bb736ddd9b83d6 Another Commit
18ed2ac1522a01 Another Commit 第2次 bad
5db7a7cb90e745 Another Commit 第4次 good
7c03a99ba38457 Another Commit
9f54462abbb991 Another Commit 第3次 good
5d1eb75377072c Another Commit
fdbfc0d403e5ac Another Commit 第1次 good
a530e7ed25173d Another Commit
ccddb96f824a0e Another Commit
2e1735d5bef6db Another Commit
ffb097e3edfa82 Another Commit
e060c0d789288f Another Commit
49774ea84ae372 Another Commit
8c992afff5e16c Another Commit
80a9b3d94237f9 Another Commit
f608824888b83b First commit

```


## level 50

你修改了一个文件的多处代码，这些代码分属于2个不同的功能，代码还没有提交到暂存区。仅提交第1个功能相关的代码到暂存区。

git add  --edit 文件名

这时git会自动打开文本编辑器,编辑的内容就是git diff命令的结果,这时你就可以编辑2个文件之间的差异,只保留要提交到暂存区的差异,而删除不需要提交到暂存区的差异,然后保存退出,git就会按你编辑过的差异把相应的内容提交到暂存区.


## level 52

你进行了多次提交,并已经推送到了远程代码库,所以你无法修改已经存在的历史,现在你想取消中间的提交.

git revert HASH-CODE 

会留下历史记录

## level 53

你决定用 git reset --hard HEAD^ 删除最后一次提交（一个不太明智的决定），然后你又反悔了，想回退到这条命令之前。请恢复被删除的提交。

git reset --hard  HASH-CODE


## level 56

你想把 https://github.com/jackmaney/githug-include-me 这个仓库的代码引入到自己项目的 ./githug-include-me 目录，这个方法不需要克隆第三方仓库，也不需要把第三方仓库的文件复制到你的项目中。

如果你想把别人的仓库代码作为自己项目一个库来使用，可以采用模块化的思路，把这个库作为模块进行管理。Git 专门提供了相应的工具，用如下命令把第三方仓库作为模块引入：