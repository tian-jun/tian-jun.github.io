# ssh
### [ssh与github](https://docs.github.com/cn/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
1. to see if existing SSH keys are present：`ls -al ~/.ssh`
2. Generating a new SSH key：`$ ssh-keygen -t ed25519 -C "juntian.job@gmail.com"`
3. When you're prompted to "Enter a file in which to save the key," press Enter. This accepts the default file location：` Enter a file in which to save the key (/Users/you/.ssh/id_algorithm): [Press enter]`
4. Adding SSH key to the ssh-agent：`eval "$(ssh-agent -s)"`
5. modify your ~/.ssh/config file to automatically load keys into the ssh-agent, and store passphrases in your keychain：`open ~/.ssh/config`
```
Host github.com
User juntian.job@gmail.com
Hostname ssh.github.com
PreferredAuthentications publickey
UseKeychain yes
IdentityFile ~/.ssh/id_ed25519
Port 443
```
6. 将 SSH 公钥复制到剪贴板：`pbcopy < ~/.ssh/id_ed25519.pub`
7. 在GitHub上添加新的SSH key：`GitHub > settings > Access > SSH and GPG keys > New SSH key > 粘贴SSH公匙 > Add SSH key`
8. test SSH：`ssh -T git@github.com`


### ssh远程登录服务器
- 密钥登陆
	- 赋予私钥文件仅本人可读权限：`chmod 400 /Users/tianjun/Desktop/Science/密钥/john_tencent_03042022`
	- 登录：`ssh -i /Users/tianjun/Desktop/Science/密钥/john_tencent_03042022 ubuntu@82.157.237.55`
- 密码登陆
	- 用户：`ssh ubuntu@82.157.237.55`
	- 密码：`john0808,`
- 注意：云服务器密码登录和密钥登录是不能同时开启的，二者是冲突的。当开启一种登录方式，另一种会默认禁用，以提高安全性。所以服务器关联密钥后将不能再使用密码登录。说明： 服务器绑定密钥默认拒绝密码登录，您需要通过密钥登录。如需要允许密码登录，要修改配置文件/etc/ssh/sshd_config，
	- `vim /etc/ssh/sshd_config`:Vim 打开sshd_config文件，键盘输入`i`，进入vim编辑器的输入模式
	- PasswordAuthentication这项改为yes，将前面#号注释符取消。保存退出并重启ssh服务既可。
	- `systemctl restart sshd`:重启ssd服务命令
- 启动jupyter notebook
	- `bash`:进入base环境,如果没有进入base环境，jupyter notebook会启动不成功
	- `jupyter notebook`:启动jupyter notebook
	- `ssh -L8888:localhost:8888 ubuntu@82.157.237.55`: 端口映射
		- `ssh-add /Users/tianjun/Desktop/Science/密钥/john_tencent_03042022`: ⚠️如果ssh报错`Permission denied (publickey)`
	- `exit`: 断开ssh链接
