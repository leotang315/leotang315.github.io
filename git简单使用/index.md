# Git简单使用



## 参考[https://www.runoob.com/git/git-basic-operations.html](https://www.runoob.com/git/git-basic-operations.html)
## 基本操作   
### git init创建新仓库

- git init
### git clone 克隆仓库

- git clone git@github.com:leotang315/aoce.git
### git config配置用户和邮箱 

- git config --list   #查看配置
- git config --global user.name "user_name"       #全局配置
- git config --global user.email  "user_email"

- git config user.name "user_name"		#单独项目配置
- git config user.email "user_email"
### git ssh 配置

- ssh-keygen -t rsa -C "user_email"  	#ssh生成
- 将用户目录下 .ssh/id_rsa.pub 文件内容拷贝到 github 或gerrit上
### git add 添加修改到暂存区

- git add . 
- git add README.md
### git reset 将暂存区恢复

- 使用当前分支上的修改覆盖暂存区，用来撤销最后一次 git add files
- git reset .
### git checkout 撤销本地更改(不包含新增文件)

- git checkout .
### git commit 提交到本地代码库

- git commit -m "提交描述"
- git commit  
### git push 提交到远程代码库

- git push <远程主机名> <本地分支名>:<远程分支名>   eg: push origin HEAD:refs/for/dev

如果分支名称相同可省略远程分支名

- git push <远程主机名> <本地分支名> 	eg: push origin master   
### git pull 拉取远程代码

### git reset 版本切换

### git status 查看工作区状态

### git log 查看提交记录
控制显示的内容

- git log  			不带参数 会显示所有历史记录（commitID,作者,日期,提交说明）
- git log -p			(--patch)	详细显示每次提交更新的差异
- git log --stat 		会显示每次提交都列出了修改过的文件，以及其中添加和移除的行数等统计信息
- git log --graph  	显示ASCII图形表示的分支合并历史
- git log --pretty=oneline  一行显示，只显示哈希值和提交说明
- git show -commitID  相关和git log -p 类似，如果知道commitID 可以更方便

控制过滤
过滤记录数

- git log -n  		会显示最近n次历史记录
- git log -n --stat  	前两个参数可以共同作用

过滤日期

- git log --since=2.weeks
- git log --since="2008-10-01" --until="2008-11-01"

过滤作者

- git log --author=leo

过滤匹配字符(添加或删除内容)

- git log -S

### git diff 查看修改

- git diff 
- git diff --cached 
- git diff <branchA> <branchB> --stat   比较两个分支不同的统计 
- git diff <branchA> <branchB>	比较两个分支不同所有文件差异
- git diff <branchA> <branchB> <file path> 比较两个分支 某文件具体差异
### git clean 删除未跟踪文件

- git clean -f  	删除未跟踪文件
- git clean -fd 	连同未跟踪的目录也删掉
- git clean -xfd 	连同.gitignore 文件中定义的文件也删除
- git clean [ -nf |-nfd | -nxfd ]	在前面加-n ，只查看，不删除

## 分支操作
### git branch 创建-删除-查看分支

### git checkout 切换分支

### git merge 合并分支

### git rebase  另一种合并分支

- git rebase <feature-branch>  
- git add . 	 ->   git rebase --continue   //如果发生冲突，则修改冲突后使用git add 添加修改,然后使用--continue 命令来继续rebase
- git rebase --abort				//如果发生冲突，放弃合并
> 

### git rebase 修改历史提交

- git rebase -i <hashA> <hashB>   // 编辑A到B所有提交（不包括A）
- git rebase -i <hashA>                  // 编辑A到HEAD所有提交（不包括A）
- git rebase -i HEAD~3                   // 编辑HEAD前3次提交
### git cherry-pick 

- git cherry-pick <commit hash>         // 转移一次提交
- git cherry-pick <feature-branch>	    // 转移feature-branch分支上最新的提交
- git cherry-pick <hashA> <hashB>    //转移多次提交
- git cherry-pick <hashA>..<hashB>   //转移从A到B的所有提交（不包括A）
- git cherry-pick <hashA>^..<hashB> // 转移从A到B的所有提交（包括A）
## 其他操作
### git tag 打标签

### git stash 暂存
### 

### gitk 图形显示

## 补充
### 单独查看文件历史
git log <filename>			查看commit 信息
git log -p <filename>    	查看具体的diff信息

### 恢复某文件
git log <filename>  找到此文件存在的commitID
git checkout [commit id] <filename>





