# Git&GitHub

## 设置git用户名/邮箱 
- `git config --global user.name "Easonxxy"`

## git连接GitHub
- 生成ssh密钥 `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`

- 手动启动ssh-agent `eval $(ssh-agent -s)`

- 将ssh密钥添加到ssh-agent

- 复制ssh密钥 `clip < ~/.ssh/id_rsa.pub`

- 测试ssh连接 `ssh -T git@github.com`

- 添加或更改ssh密码 `ssh-keygen -p`