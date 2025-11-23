### 常用linux命令

1. cd:改变目录; 后面接当前目录下文件夹名
2. cd ..:回退
3. pwd:显示当前目录路径 绝对路径
4. ls:列出当前目录内容,包含文件夹和文件;(ll功能相似,内容更加丰富)
5. touch:创建新文件到当前目录
6. rm:删除文件
7. mkdir:创建新的文件夹
8. rm -r:删除一个文件夹
9. mv:移动文件 第一个参数是目标文件,第二个参数是目标目录
10. reset:初始化终端
11. clear:清屏
12. history:查看历史命令
13. help:查看帮助
14. exit:退出
15. #注释

### git配置

git config -l:查看git的配置

系统配置

用户配置
git config --global --list

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
git init 创建本地仓库  
git clone 克隆远端仓库 参数是远端仓库url


    