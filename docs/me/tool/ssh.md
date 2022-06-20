# ssh链接github
 `$ ssh-keygen -t ed25519 -C "juntian.job@gmail.com"`




### ssh远程登录
#### 密钥登陆
赋予私钥文件仅本人可读权限
	chmod 400 /Users/tianjun/Desktop/Science/密钥/john_tencent_03042022
终端执行如下命令就可以登录了
`ssh -i /Users/tianjun/Desktop/Science/密钥/john_tencent_03042022 ubuntu@82.157.237.55`
#### 密码登陆
用户：`ssh ubuntu@82.157.237.55`
密码：`john0808,`
⚠️云服务器密码登录和密钥登录是不能同时开启的，二者是冲突的。当开启一种登录方式，另一种会默认禁用，以提高安全性。所以服务器关联密钥后将不能再使用密码登录。说明： 服务器绑定密钥默认拒绝密码登录，您需要通过密钥登录。如需要允许密码登录，要修改配置文件/etc/ssh/sshd_config，
	vim /etc/ssh/sshd_config
键盘输入`i`
PasswordAuthentication这项改为yes，将前面#号注释符取消。保存退出并重启ssh服务既可。重启sshd服务命令：systemctl restart sshd。
### 进入base环境
`bash`
### 启动jupyter notebook
```python
jupyter notebook
```
⚠️如果没有进入base环境，jupyter notebook会启动不成功
### 端口映射
在本地账户输入
	ssh -L8888:localhost:8888 ubuntu@82.157.237.55
⚠️如果ssh报错`Permission denied (publickey)`，命令行输入
	ssh-add /Users/tianjun/Desktop/Science/密钥/john_tencent_03042022
### 断开ssh链接
	exit