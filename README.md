# gilab
#生成 SSH 密钥
ssh-keygen -t ed25519 -C "your_email@example.com"
cat ~/.ssh/id_ed25519.pub
输出类似：ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIJx7m... your_email@example.com

nano ~/.ssh/config
Host gitlab.cern.ch
    HostName gitlab.cern.ch
    User git
    Port 7999
    IdentityFile ~/.ssh/id_ed25519  # 👈 修改为您的私钥路径
    IdentitiesOnly yes
Ctrl+O → Enter → Ctrl+X
chmod 600 ~/.ssh/id_ed25519  # 替换为您的私钥文件名
ssh -T git@gitlab.cern.ch
# 将密钥添加到ssh-agent避免重复输入密码
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
