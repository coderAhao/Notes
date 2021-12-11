#### 第一章: git基础

##### 第1节: 基本概念

- 集中式(svn)
    - 特点:保存的是版本之间的差异,需要内存空间小,但回滚(回到历史)速度慢
    - 优点:代码存放在单一的服务器上 便于项目管理
    - 缺点:服务器宕机则代码得不到保障 服务器爆炸则整个项目历史记录会丢失；分支只能在服务器上创建

- 分布式(git)
    - 特点:保存的并不是版本之间的差异,而是将每个版本的索引都进行了保存,需要内存稍大但回滚速度快
    - 优点: 版本控制在本地进行开发,断网也不影响；使用github进行团队协作,每个客户端保存的都是整个项目；可在本地创建分支；尽可能添加数据而不是删除或修改

##### 第2节: 安装配置git

- 安装包可直接安装,默认为C盘可自己更改至其他盘
- 一路点击next,中间有些需勾选也可不勾选,具体百度
- 配置文件:
    - 控制台输入“git config --global user.name '电脑名'”
    - 控制台输入“git config --global user.email '具体邮箱'” 
    - 注:--global此用户(一个系统可有多个用户)安装(即用户级别) --system此电脑系统安装(即系统级别)
    - “git config”后不写则默认在当前项目git目录中的配置文件(即项目级别)
- 检查配置: “git config --list”
- 重新配置: 再次输入配置步骤更改电脑名及邮箱
- 区域:工作区 暂存区 版本库
- 对象:git对象 树对象 提交对象
- git流程: 工作目录先到版本库,生成git对象,再到暂存区

##### 第3节: git文件夹里的文件说明

- hooks 钩子,类似生命周期
- info 包含一个全局性排除文件(即git不需要进行管理的文件夹)
- logs 保存的日志信息
- objects 存储所有的数据内容
- refs 指向存储数据(分支)的提交对象的指针
- config 配置信息
- description 对仓库的描述信息
- HEAD 指示目前被捡出的分支
- index 文件保存暂存区的信息



------

#### 第二章: 命令操作

##### 第1节: Linux基础命令

- “clear” 清屏
- “echo "message"” 控制台打印信息(类似console)
- “> fliename” 创建文件
- “ll” 将当前文件夹下的子文件和子文件夹平铺在控制台(过滤掉隐藏文件)
- “ls” 列出当前文件夹里的所有文件
- “find filename” 将对应文件下的子孙文件和子孙文件夹平铺在控制台
- “find filename -type f” 将对应文件下的文件平铺在控制台(即过滤掉文件夹)
- “rm filename” 删除文件
- “mv oldname newname” 重命名文件
- “cat fileURL” 查看指定文件的内容
- “vim fileURL” 修改指定文件内容
    - 再按“i”进入插入模式进行文件编辑
    - 按“esc”退出编辑
    - 再按“:”紧跟以下命令
        -  “q!” 强制退出,不保存
        - “wq” 保存退出
        - “set nu” 设置行号

- “mkdir fileName” 创建文件夹(make directory)
- “cd fileURL” 切换当前工作目录(change directory)
- “ctr+insert” 复制 (另:选中即复制)
- “shift+insert” 粘贴 (另:鼠标中键也可粘贴)
- “tail -n [num] fileName” 只显示fileName文件的最后num行

##### 第2节: git本地操作(高层命令)

- “git init”将目录变为仓库
- “git add fileName” 添加文件到暂存区
    -  “git add fileName1 fileName2”可有选择性的添加
    -  “git add .” 将所有文件添加到暂存区

- “git commit -m fileName” 文件提交到仓库(提交前必须暂存)  提交方式1,不写说明信息
    - “git commit -m "注释信息"” 提交方式2 “-m后跟注释信息”
    - “git commit” 提交方式3 进入编辑界面,编写注释信息
    - “git commit -a” 跳过暂存区直接提交(必须是原来已经添加过的)
-  “git status” 查看文件状态  文件状态:已跟踪(分为已提交、已暂存、已修改) 未跟踪
- “git diff” 查看已修改但未暂存的内容
    - “git diff --stage(或catch)” 查看已暂存但未提交的内容
- “cat fileName” 查看文件内容
- “git log” 查看提交的历史记录详细信息
    - 内容过多时“空格向下翻页 b向上 q退出”
    - “git log --graph” 显示图形化的日志
    - “git log --pretty=oneline” 显示历史记录,但仅显示完整哈希值和注释信息
    - “git log --oneline” 显示历史记录,但仅显示哈希值前七位和注释信息
    - “git reflog” 显示历史记录,当前要跳回到指定状态需要的步数(HEAD@{number} num为步数)
- “echo "mes" | git hash-object -w --stdin” 向数据库写入内容并返回文件的哈希值
    - “mes”可写为“"mes" > filename”即新建文件并写入
- “git hash-object -w fileURL” 保存指定文件内容并获取哈希值(每个文件都会以哈希值区分)
-  “git cat-file -t 序列号” 查看提交的类型
- “git cat-file -p 序列号” 查看提交时的说明信息
- “git ls-files -s”查看暂存区
- “git config --global alias.别名 原名” 起别名
    - 如“git config --global alias.ci commit” 以后输入“git commit”可写为“git ci”
- “git config --list” 查看配置信息

##### 第3节: 分支

- 分支:本质是一个提交对象
    - HEAD:是一个指针,默认指向master分支 (指向最新提交对象的一个指针)
    - 切换分支就是让HEAD指向不同的分支
    - 每次有新的提交时HEAD都会带着当前指向的分支向前移动
    - 分支管理的本质是创建和移动指针
- “git branch” 显示分支列表
    - “git branch -v” 显示分支的哈希值及注释信息
- “git branch branchName ” 在当前提交对象上创建分支
- “git checkout branchName” 切换分支
    - 切换分支时,当前分支一定得是已提交状态,否则此分支上未提交的暂存会被带到另一分支上造成污染
    - git checkout -b branchname 创建一个新分支并切换到这里
    - 若忘记创建分支,当在主分支上写好代码后可将其迁移到此分支再进行提交
- “git branch -d branchName” 删除空的或已被合并的分支
    - 注:不可删除当前所在的分支,应切换到别的分支上时再去删除
- “git branch -D branchName” 强制删除分支
- “git merge branchName” 将分支合并到当前分支上
- “git branch --merged” 查看合并到当前分支的分支列表
    - 注:一旦出现在此列表上,说明那些分支已被合并,应该将其删除
- “git branch --no-merged” 查看没有合并到当前分支的分支列表
    - 注:一旦出现在此列表上,应该观察下这些分支是否需要合并
- 解决分支冲突: 编辑冲突的文件,删除特殊指示符号；修改文件；添加到暂存区并提交
- 分支种类:
    - 主干分支master:主要负责正在运行的生产环境代码,永远保持与正在运行的生产环境一致
    - 开发分支develop:主要负责管理正在开发过程中的代码,一般为最新代码
    - bug修理分支hotfix:主要负责管理生产环境下出现的紧急修复代码,从主干分出
    - 准生产(预发布)分支release:版本上线前从develop分支中分出,进行最后阶段的集成测试
    - 功能分支feature:为了不影响开发,将中长期开发模块从develop分支中独立出来

- 存储
    - 目的:当在一个分支上做了部分工作后需切换到另一分支,但工作还未完成不想进行提交,可使用存储命令
    - “git stash” 将未完成的修改保存到栈上
    -  “git stash list” 查看存储
    -  “git stash apply 栈名” 将栈顶的工作内容还原但不让工作内容出栈 重新应用栈
    - “git stash drop 栈名” 移除栈

##### 第4节: 撤回操作

- 工作区撤销:
    - “git restore -- fileName” 撤销修改
        - 若内容修改但未放入暂存区则会将工作区的修改撤销
        - 若提交到暂存区又进行修改则会撤销修改回到已提交暂存区的状态
    - “git restore fileName”可将删除的文件再恢复
        - 删除后的文件只要未commit都能恢复
    - “git checkout -- filename” 危险命令,虽然也是撤销但是是用另一个文件来覆盖它

- 暂存区撤销: 将文件从暂存区撤回到工作区
    - “git reset --hard HEAD^” 后退到上一个版本(注:只能后退不可前进)
    - “git reset --hard HEAD^^” 后退到上二个版本
    - “git reset --hard HEAD~num” 后退到上num个版本
    - “git reset --hard HEAD 版本号” 回退到指定版本
    - “git reset --hard hash” 回到指定哈希值版本
    - “git reset HEAD filename” 撤销暂存区修改
    - reset的三个参数“soft mixed hard”
        - git reset --soft HEAD^ 只动head且带着分支移动(只改变工作区)
        - git reset --mixed HEAD^ 动head和暂存且带着分支移动(工作区和暂存区会改变)
        - git reset --hard HEAD^ 动head、暂存和工作目录且带着分支移动(工作、暂存和本地库均会改变)
        - --hard是reset命令的危险用法,因为它会强制覆盖工作文件目录,不可找回

- 版本库撤销:  “git commit --amend” 修改提交注释信息
- “git checkout commithash”与“git reset --hard commithash”的区别
    - 前者只动head 对工作目录是安全的
    - 后者动head且带着分支一起走 强制覆盖工作目录

##### 第5节: 远程操作

- “git remote -v” 查看远程地址
- “git remote add [别名] [远程仓库地址]” 添加新的远程仓库(并为其起别名)
    - 如:“git remote add origin git地址”
- “git push [别名] [分支]” 推送本地仓库到远程仓库(分支可为主分支master或其他分支)
    - 如:“git push -u origin master” (即将本地的master分支推送到远程的origin仓库中,若要推送其他分支可将master改为其他分支名)
    - 推送过程:
        - git remote add origin(别名) XXXX(远程仓库地址)
        - 第一次推送时：git push -u origin master (-u是指定origin为默认主分支)
        - 之后推送时若推送主分支只需：git push origin master(或直接git push)
        - 注：代码写完远程推送时先将分支提交推送到远程,再切换到主分支上并将刚才的分支进行合并,再将主分支推送到远程

- “git clone [远程仓库地址]” 克隆远程仓库
    - 效果: 把远程仓库下载到本地、创建clone远程地址别名、初始化本地库
    - “git clone file1URL file2URL”将file1的内容克隆到file2
    - 在克隆后,会自动跟踪被克隆文件的地址,pull命令知道从哪取回新的提交
- “git fetch [远程别名] [远程分支名]” 将远程内容下载到本地
- “git merge [远程别名/远程分支名]” 将下载下来的内容与本地进行合并
- “git pull [远程名] [远程分支名]” 将远程内容下载到本地并进行合并(fetch和merge的结合)
- clone和pull的区别:
    -  clone: 本地无仓库时可将远程仓库整个下载下来
    - pull: 本地需要有个仓库(即有.git文件)；团队协作时,将远程仓库新的commit(更改提交)下载下来

- 冲突: 
    - 推送时,一般都是pull再push
    - 因为如果不是基于Github远程库的最新版所做的修改则不能推送,必须先拉取
    - 比如两个人同时拉取后同时推送就会冲突,应为A推送后B先拉取再推送

##### 第6节：打tag标签

- 标签: 轻量标签、附注标签
- “git tag” 列出标签
- “git tag -l  '版本号*' ” 匹配此版本号之后的所有
- “git tag 版本号” 创建标签
- “git tag -d 版本号” 删除标签