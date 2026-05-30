# Git 操作完整指南（从入门到实战）

------

# 一、Git 核心概念

```text
工作区（Working Directory）
↓
暂存区（Staging Area）
↓
本地仓库（Repository）
↓
远程仓库（Remote）
```

------

# 二、初始化与克隆

## 1. 初始化仓库

```bash
git init
```

------

## 2. 克隆远程仓库

```bash
git clone 仓库地址
```

指定目录：

```bash
git clone 仓库地址 自定义目录名
```

------

# 三、基础开发流程（最常用）

## 1. 查看状态

```bash
git status
```

------

## 2. 添加文件

```bash
git add 文件名
git add .    # 添加全部
```

------

## 3. 提交代码

```bash
git commit -m "feat: 描述信息"
```

------

## 4. 查看提交记录

```bash
git log --oneline
```

------

# 四、分支管理

## 1. 查看分支

```bash
git branch
```

------

## 2. 创建分支

```bash
git branch dev
```

------

## 3. 创建并切换

```bash
git checkout -b feature-xxx
```

或：

```bash
git switch -c feature-xxx
```

------

## 4. 切换分支

```bash
git checkout master
```

------

## 5. 删除分支

```bash
git branch -d feature-xxx
```

------

# 五、远程仓库操作

## 1. 查看远程仓库

```bash
git remote -v
```

------

## 2. 添加远程仓库

```bash
git remote add origin 仓库地址
```

------

## 3. 推送代码

```bash
git push origin master
```

首次推送：

```bash
git push -u origin master
```

------

## 4. 拉取代码

```bash
git pull origin master
```

等价：

```bash
git fetch
git merge
```

------

# 六、标准团队开发流程（重点）

```bash
# 1. 更新主分支
git checkout master
git pull origin master

# 2. 创建功能分支
git checkout -b feature-xxx

# 3. 开发并提交
git add .
git commit -m "feat: xxx"

# 4. 推送分支
git push origin feature-xxx

# 5. 合并到 master
git checkout master
git pull origin master
git merge feature-xxx
git push origin master
```

------

# 七、合并分支

```bash
git checkout master
git merge feature-xxx
```

------

# 八、冲突处理

冲突标记：

```text
<<<<<<< HEAD
当前分支代码
=======
目标分支代码
>>>>>>> feature-xxx
```

处理流程：

```bash
# 修改文件后
git add .
git commit
```

------

# 九、忽略文件（.gitignore）

## 示例

```gitignore
# 忽略PDF
*.pdf

# 忽略IDE
.idea/
.vscode/

# 系统文件
.DS_Store
```

------

## 已被跟踪文件取消追踪

```bash
git rm --cached 文件名
```

------

# 十、常用高级操作

## 1. fetch（推荐）

```bash
git fetch
git merge
```

------

## 2. rebase（线性历史）

```bash
git checkout feature-xxx
git rebase master
```

------

## 3. 撤销操作

### 撤销 add

```bash
git reset 文件名
```

------

### 撤销 commit（未 push）

```bash
git reset --soft HEAD~1
```

------

### 强制回退（危险）

```bash
git reset --hard HEAD~1
```

------

# 十一、删除远程分支

```bash
git push origin --delete feature-xxx
```

------

# 十二、常见错误与解决

------

## 1. clone 失败（目录已存在）

```text
fatal: destination path already exists
```

解决：

```bash
rm -rf 目录名
```

------

## 2. 空仓库提示

```text
You appear to have cloned an empty repository
```

👉 正常，需要自己提交代码

------

## 3. https 报错

```text
remote-https is not a git command
```

👉 Git 安装或 PATH 问题

------

## 4. 嵌套仓库错误

```text
does not have a commit checked out
```

解决：

```bash
rm -rf 子目录/.git
```

------

# 十三、最佳实践（非常重要）

------

## 1. 仓库结构建议

```text
Notes/
├── kaoyan/
├── cs/
├── project/
└── .git
```

👉 一个项目一个仓库（避免嵌套）

------

## 2. 提交规范

```text
feat: 新功能
fix: 修复问题
refactor: 重构
docs: 文档
```

------

## 3. 推荐掌握的核心命令

```bash
git add .
git commit -m ""
git pull
git push
git checkout -b xxx
git merge xxx
```

------

# 十四、Summary

```text
Git = 版本管理 + 分支隔离 + 合并协作
```

