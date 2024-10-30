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


4. 工作区、版本库
`.git`：版本库里面有：stage/index 暂存区、指针HEAD、分支master

逻辑：
第一步是用git add把文件添加进去，实际上就是把文件修改添加到暂存区；

第二步是用git commit提交更改，实际上就是把暂存区的所有内容提交到当前分支。

因为我们创建Git版本库时，Git自动为我们创建了唯一一个master分支，所以，现在，git commit就是往master分支上提交更改。

你可以简单理解为，需要提交的文件修改通通放到暂存区，然后，一次性提交暂存区的所有修改。

如果：工作区没有修改+暂存区为空，输入`git status`，可以得到：
```bash
$ git status
On branch master
nothing to commit, working tree clean
```

### 管理修改

Git管理的是“修改”，而不是文件

```bash
# 流程：
第一次修改文件
git add <file>
第二次修改文件
git commit -m 'change file'

# 上述会导致的结果
版本回退时，只能回退到第一次修改的内容
因为git commit -m '' 只是将第一次修改的内容提交上去

为了把第二次修改的内容也提交上去
git add 第一次修改的文件
git add 第二次修改的文件
git commit -m ''
```

### 撤销修改

撤销工作区的修改:
工作区修改，未提交到暂存区
撤销命令：`git checkout -- <file>` 或 `git restore <file>`
工作区修改，并提交到暂存区
```bash
# --staged 将暂存区的文件从暂存区撤出，但不会更改文件
git restore --staged <file>
# 表示将在工作区但是不在暂存区的文件撤销更改
git restore <file>
```

撤销暂存区的修改:
```bash
git restore --staged <file>
git restore <file>
```


### 删除文件

2种情况：
1. 删除工作区文件，然后删除版本库的文件
先删除本地文件
git status
git rm <file>
git commit -m "rm xxxfile"

2. 误删工作区文件，需要恢复
git checkout -- <file>