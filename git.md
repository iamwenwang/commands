<font face="Consolas" size=2>

###### git 常用命令

在本地创建分支 dev 并拉取 develop 远程分支
`git checkout -b dev（本地分支名称） origin/develop（远程分支名称）`

查看分支
所有分支：`git branch -a`
本地分支：`git branch`
远程分支：`git branch -r`

切换分支
`git checkout dev（本地分支名称）`

删除分支
`git branch -D dev（本地分支名称）`
`git push origin --delete dev（远程分支名称）`

###### git windows 环境设置多账号

1. 删除全局账号配置
   `git config --global --list`
   `git config --global --unset user.name`
   `git config --global --unset user.email`
2. 生成 SSH KEY
   `ssh-keygen -t rsa -C "user1@email.com"`
   `ssh-keygen -t rsa -C "user2@email.com"`
   生成 rsa/ras.pub 文件
3. Github 部署 SSH KEY

   - Github->Settings->SSH and GPG keys->New SSH key->Key 栏中填入 ras.pub 内容
   - 将新 SSH 密钥添加到 ssh-agent
     `eval $(ssh-agent -s)`
     `ssh-add ~/.ssh/id_rsa`
   - 测试 SSH 密钥是否生效
     `ssh -T git@github.com`
     提示：You've successfully authenticated 表示成功

4. 配置 config 文件

   ```config
   Host 　　 主机别名
   HostName 　　 服务器真实地址
   IdentityFile 　　 私钥文件路径
   PreferredAuthentications 　　认证方式
   User 　　 用户名

   Host user1.github.com
   HostName github.com
   IdentityFile C:\\Users\\{username}\\.ssh\\id_rsa_1
   PreferredAuthentications publickey
   User user1

   Host user2.github.com
   HostName github.com
   IdentityFile C:\\Users\\{username}\\.ssh\\id_rsa_2
   PreferredAuthentications publickey
   User user2
   ```

   测试 SSH 是否生效
   `ssh -T git@user1.github.com`
   `ssh -T git@user2.github.com`
   提示：You've successfully authenticated 表示成功

5. 使用远程仓库地址拉取代码

   - 需要使用远程仓库地址，如果原先使用 HTTPS 通信，则需要修改远程仓库地址
   - 每个仓储需要单独配置 name/email
