1. 配置Git

```bash
# -global 全局配置；一次配置，整机生效
git config --global usr.name ""
git config --global usr.email ""

# 查看配置信息, q 退出
git config --list
```

M：已修改（Modified） - 文件已被修改但还没有被添加到暂存区

A：已添加（Added） - 文件已经被添加到暂存区，但还没有被提交

D：已删除（Deleted） - 文件已经被删除，并且已经被标记为删除，但还没有提交

R：已重命名（Renamed） - 文件已经被重命名，这也算作是一种修改，需要被添加到暂存区

C：已复制（Copied） - 文件已经被复制，这也算作是一种修改，需要被添加到暂存区

U：已更新但未融合（Updated but Unmerged） - 这表示一个文件已经被更新了，但在合并时发生了冲突，需要手动解决冲突后再标记为已解决

2. 添加文件和提交

```bash
git add <file>

# 添加说明注释
git commit -m ""

# 不添加说明注释
git commit

# 查看修改文件的内容
git diff <file>

# 查看当前仓库的状态
git status
```


3. 修改文件后，git再查看修改了哪里

```bash
Impossible7@DESKTOP-77STT21 MINGW64 /e/GitRepository/LearningGit (master)
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   Learning.md

no changes added to commit (use "git add" and/or "git commit -a")

Impossible7@DESKTOP-77STT21 MINGW64 /e/GitRepository/LearningGit (master)
$ git diff Learning.md
diff --git a/Learning.md b/Learning.md
index 81a5c5a..0335e19 100644
--- a/Learning.md
+++ b/Learning.md
@@ -41,3 +41,5 @@ git status

 测试修改文件

+
+

```

在`@@ -41,3 +41,5 @@ git status`下面可以看到具体修改的内容

测试版本回退：
版本1
版本2
版本3


```bash
# 查看修改内容
git log

# 精简提交日志输出信息
git log --pretty=oneline

commit 就是一个“快照”

# 查看输出信息
Impossible7@DESKTOP-77STT21 MINGW64 /e/GitRepository/LearningGit (master)
$ git log --pretty=oneline
cf5d3083721073f9c5954588225db7777c1c2962 (HEAD -> master) 版本3
f53565cc3753eac031b0d8200bfaa0b0c5b67ab3 版本2
bd379362699e2bd24911f1b4299a017d78c1079d 版本1
1ef0cdffaeb17886d4b73913a31a0a062e476b5d 测试修改文件
88bbb95213e4a4fe8dc72820c2c45a6d53ee6df7 Learning.md
abece97ab22133e2ac6ef8a4a6d82f3e42a7df37 change readme.md

# 前面为16进制，commit id（版本号）

# 回退版本
git reset --hard HEAD^
get reset --soft
get reset --mixed

--hard 会回退到上个版本的已提交状态
--soft 会回退到上个版本的未提交状态
--mixed 会回退到上个版本已添加但未提交的状态

HEAD^ 上版本
HEAD^^ 上上版本
HEAD~100 上100版本

# 穿越回去
git reset --hard HEAD^

# 穿越回来
git resit --hard cf5d3

# 使用过的命令
git reflog
```

