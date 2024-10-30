根据git status显示的内容知道是在 工作区、暂存区、已经提交的 这三个区域的哪里进行了修改

```bash
# 这代表：在暂存区
# 输出每一句话的意思：
# 在master分支
# 要提交的更改：
# （使用“git restore--stage<file>…”取消分页）
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   Learning.md

# 这代表在工作区
# 在master分支
# 未进行提交的更改：
# （使用“git add<file>…”更新将提交的内容）
# （使用“git restore<file>…”放弃工作目录中的更改）
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   Learning.md

```