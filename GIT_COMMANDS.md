# Git 初始化与推送命令

以下是本次执行的核心 Git 命令，使用 PowerShell。
远程仓库已有 main 分支，所以先同步已有提交，再提交本说明文件。
这些命令用于记录本次操作，不需要重复执行。

```powershell
# 确认已安装 Git。
git --version

# 检查远程默认分支及提交。
git ls-remote --symref https://github.com/Kch71325466/git-text.git HEAD
git ls-remote https://github.com/Kch71325466/git-text.git

# 初始化当前文件夹，使用 main 分支。
git init -b main

# 添加 GitHub 远程仓库。
git remote add origin https://github.com/Kch71325466/git-text.git

# 下载远程历史。
git fetch origin

# 当前文件夹为空且没有本地提交，将本地 main 对齐到远程 main。
# 已有本地提交时不可直接照搬此命令。
git checkout -B main origin/main

# 将本说明文件加入暂存区。
git add GIT_COMMANDS.md

# 检查暂存区的空白字符问题，并查看变更摘要。
git diff --cached --check
git diff --cached --stat

# 使用已有的 Git 用户配置创建提交。
git commit -m "docs: record annotated Git initialization and push commands"

# 推送 main，并设置上游跟踪关系。
git push -u origin main

# 检查工作区状态和最新提交。
git status --short --branch
git log -1 --oneline

# 比较远程 main 与本地 HEAD 的提交编号，确认推送成功。
git ls-remote origin refs/heads/main
git rev-parse HEAD
```
