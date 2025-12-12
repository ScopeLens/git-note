# git-note
git学习笔记

安装教程:[文章地址](https://blog.csdn.net/qq_45281589/article/details/134650456)

- [git-note](#git-note)
    - [git配置](#git配置)
    - [git基本理论](#git基本理论)
    - [仓库创建](#仓库创建)
      - [创建本地仓库](#创建本地仓库)
      - [拉取远端仓库](#拉取远端仓库)
    - [基本操作](#基本操作)
      - [基础的工作流程](#基础的工作流程)
      - [回退提交](#回退提交)
        - [版本回滚](#版本回滚)
        - [本地文件回滚](#本地文件回滚)
    - [分支管理](#分支管理)

### git配置

系统配置:git config -l:查看git的配置

用户配置:git config --global --list

### git基本理论

>工作区域
四个工作区
1. Working Directory 工作目录
2. Stage(index) 暂存区
3. Repository 本地仓库 HEAD 指向主分支
4. Remote Directory 远端仓库

从上到下命令  *git add -> git commit ->git push*  
反过来 *git checkout <- git reset <- git pull*

git管理的文件存在三种状态:modified(已修改),staged(已暂存),committed(已提交)  


### 仓库创建

#### 创建本地仓库
git init  
语法:`git init [目录]`  
作用:如果不加目录参数就会直接将当前目录下初始成一个仓库,创建.git文件,加了之后就会在特定目录下创建

同步远端仓库
1. 远端仓库例如github,构建一个新的远端仓库,注意仓库中不需要存在任何文件,防止与本地文件存在冲突  
2. 使用`git remote add`命令,将远端仓库的url命名为`origin`(约定名称)
3. 添加完毕之后通过`git remote -v`来验证是否添加成功(添加错误可以使用`git remote rm [name]`移除)
4. 之后通过`git push`命令同步仓库文件  
   本地仓库分支会影响这个提交命令:`git push -u origin [本地分支:master/main]`  
   `-u`是为了设置本地分支跟踪远程的同名分支

#### 拉取远端仓库

git clone  
语法:`git clone [远程仓库地址URL]`  
作用:将远端仓库拉取到本地,直接在指令工作目录中创建新的仓库

### 基本操作

#### 基础的工作流程
1. `git pull`拉取最新的代码
2. 工作完毕之后使用`git status`查看暂存区有哪些文件发生了修改,新增
3. 使用`git add`添加文件到本次想要commit的内容中
4. `git commit`直接提交,不过一般会带上`-m [提交信息]`,提交到本地仓库
5. 确认完毕之后`git push`到远程仓库

#### 回退提交

##### 版本回滚

git reset  
语法:`git reset [选项] [目标版本/commit_id]`  
作用:回滚到对应版本  
选项:  
`--hard`:表示回滚到目标版本已提交的状态,会彻底丢弃所有修改  
`--soft`:表示回滚到目标版本的未提交状态  
`--mixed`:表示回滚到目标版本未添加状态,会保留目录文件,但是清空暂存区

git log  
语法:`git log`  
作用:查看当前分支的commit记录


git reflog  
语法:`git reflog`  
作用:查看历史记录,是所有的记录,相当于是后悔药,防止你回滚了但是又后悔了,可以查看历史所有的commit的id

在git中用`HEAD`表示当前版本,上个版本是`HEAD^`,上上个版本就是`HEAD^^`,更多就难写了,用`HEAD~N`,N表示前多少个版本  

回滚代码使用`git reset`,例如我要回滚到上一个版本`git reset --hard HEAD^`

##### 本地文件回滚

git restore  
命令:`git restore [选项] [文件地址]`  
作用:会将指定文件回滚到上一次提交或者暂存的状态,就是回滚到上一次追踪到的记录  
选项:  
`--staged`:将目标文件从暂存区回滚到工作区  
实例:`git restore .`丢弃当前目录下所有未暂存的文件修改

git rm  
命令:`git rm [选项] [目标文件]`  
作用:删除文件,或者放弃追踪文件  
选项:  
`--cached`:将文件移出版本控制,但是保留本地文件,如果不加这个选项实际就是执行了`rm`+`git add`

### 分支管理
