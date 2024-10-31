# 远程仓库

## 添加远程库

1. 本地生成密钥，公钥添加到Github上，然后本地仓库与远程仓库关联起来
`git remote add origin git@github.com:账户名/仓库名.git`
`origin`为远程仓库的名字

2. 推送到远程仓库repository
第一次推送`git push -u origin master`，当前分支是master。
以后推送`git push origin master`

3. 删除远程仓库
第一，查看远程仓库信息、解除本地与远程仓库的关联

```bash
$ git remote -v
origin  git@github.com:michaelliao/learn-git.git (fetch)
origin  git@github.com:michaelliao/learn-git.git (push)

git remote rm origin
```

第二，远程仓库删除项目。

需要删除某个文件：本地先删除该文件，然后与远程仓库同步，`git commit -m "remove fiel"`

4. ssh-agent：控制用来保存公钥身份验证所使用的私钥的程序。
使用场景：
    a. 使用不同的密钥连接到不同的主机时，需要手动指定对应的密钥。ssh-agent 可以帮助我们选择对应的密钥进行认证，不用手动指定密钥即可进行连接。 
    b.当私钥设置了密码，我们又需要频繁的使用私钥进行认证时，ssh-agent 可以帮助我们免去重复的输入密码的操作。



## 从远程库克隆
使用命令
` git clone git@github.com:michaelliao/gitskills.git`
