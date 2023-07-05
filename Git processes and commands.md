# Git常用流程与命令收集

## 1 新建
### 1.1 新建本地仓库并推送至远程
```bash
# 创建本地仓库
# 切换到仓库目录，执行
git init
# 添加文件到暂存区
git add .
# 提交文件到工作区
git commit -m "commit msg"
# 添加远程仓库
git remote add origin remoteUrl
# 推送
git push origin localTag
```
### 1.2 新建本地分支并推送到远程
```bash
# 从当前分支新开分支
git branch localTag
# 切换分支
git checkout localTag
# 创建并切换分支
git checkout -b localTag
# 将本地新分支推送到远程分支
git push origin localTag:remoteTag
```

### 1.3 克隆远程分支到本地
```bash
git clone remoteUrl
# 支持HTTP、SSH、Git等、本地等
git clone http[s]://example.com/path/to/repo.git
git clone http://git.example.net/yiibai/sample.git
git clone ssh://example.com/path/to/repo.git
git clone git://example.com/path/to/repo.git
git clone /opt/git/project.git 
git clone file:///opt/git/project.git
git clone ftp[s]://example.com/path/to/repo.git
git clone rsync://example.com/path/to/repo.git
```

## 2 删除

### 2.1 删除远程分支
```bash
# 删除
git push origin --delete remoteTag
# 推送空分支到远程
git push origin :remoteTag
```

### 2.2 删除本地分支
```bash
git branch -d xxx
```
### 2.3 删除`git add`的文件
```
git rm --cache filename
```
### 2.3 清除所有修改
```bash
# 已发生add
git reset .
# 未发生add或者commit 
git checkout .
# 删除新建的文件和文件夹
git clean -df
```


## 3 修改
### 3.1 合并分支
```bash
(develop)
git add .
git commit -m "commit msg"
git push origin develop
git checkout master
(master)
git pull origin master
git checkout develop
(develop)
git merge master
# 解决冲突
git add .
git commit -m "commit msg"
git push origin develop
```
### 3.2 修改commit信息
```Bash
# commit 并使用上次commit Msg
git commit --amend --no-edit
# 修改当前commit Msg
git commit --amend -m "commit msg"
```

### 3.3 回滚远程分支
```bash
# 先更新到本地
git reset --hard <log id>
git push -f origin <local tag>:<remote tag>
```

### 3.4 更新到远程的其他分支
```bash
git push master:obn
```

### 3.5 拉取远程代码并合并到当前分支
```bash
# 从远程获取代码库
git fetch
# 当前库仅落后于远程
git pull
# remoteTag和localTag有分歧
git merge origin/remoteTag localTag
# 处理冲突
# 提交到工作区
git commit -m "commit msg"
# 提交到远程
git push origin localTag:remoteTag
```

### 3.6 更新远程仓库地址
```bash
# 设置远程url地址
git remote set-url origin <url>
# 查看远程信息
git remote -v
```

## 4 查看
### 4.1 查看
```bash
# 显示工作目录和暂存区的状态
git status
# 查看日志
git log
# 查看多分支情况
git log --oneline --graph --decorate --all
```
## 5 其他

### 5.1 更新中警告
```
git config --global core.autocrlf true
```
### 5.2 忽略某个在库中的配置文件
```bash
# 忽略
git update-index --assume-unchanged gen.bat
# 恢复追踪
git update-index --no-assume-unchanged gen.bat
# 查看当前被忽略的文件
git ls-files -v | grep -e "^[hsmrck]"
```
### 5.3 git commit 格式建议
[参看资料1](https://zhuanlan.zhihu.com/p/400870942)
- commit message格式
```text
<commit类型>(影响范围): 具体描述
<type>(<scope>): <subject>
举例 fix(DAO): fixed invalid user table indexes.
```
- type
```text
feat    : 新增功能
fix     : 修复bug
docs    : 仅仅修改了文档，比如 README, CHANGELOG等等
test    : 增加/修改测试用例，包括单元测试、集成测试等
style   : 修改了空行、缩进格式、引用包排序等等（不改变代码逻辑）
perf    : 优化相关内容，比如提升性能、体验、算法等
refactor: 代码重构，「没有新功能或者bug修复」
chore   : 改变构建流程、或者增加依赖库、工具等
revert  : 回滚到上一个版本
merge   : 代码合并
```

