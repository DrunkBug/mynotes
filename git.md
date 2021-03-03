## git配置ssh
1.设置ssh配置文件，C:\Users\xxx\.ssh\config。  
2.在.ssh\目录下生成密钥  
	ssh-keygen -t rsa -C "这里换上你的邮箱"，一路回车。  
3.github上个人ssh配置中New SSH key，将id_rsa内容复制其中。  
4.注意config中配置的代理。  
	**-H http代理， -S socks代理，-T tcp代理。**
	<br/>
- config文件
```conf
# 这里的 -a none 是 NO-AUTH 模式，参见 https://bitbucket.org/gotoh/connect/wiki/Home 中的 More detail 一节
ProxyCommand connect -H xxx.xxx.xxx.xxx:xxxx -a none %h %p

Host github.com
  User git
  Port 22
  Hostname github.com
  # 注意修改路径为你的路径
  IdentityFile "C:\Users\admin\.ssh\id_rsa"
  TCPKeepAlive yes

Host ssh.github.com
  User git
  Port 443
  Hostname ssh.github.com
  # 注意修改路径为你的路径
  IdentityFile "C:\Users\admin\.ssh\id_rsa"
  TCPKeepAlive yes
```