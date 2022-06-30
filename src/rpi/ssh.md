# 使用ssh

## 一、使用puttygen

```admonish info
直接参考以下文章：[How to generate public and private ssh key using putty](https://docs.oracle.com/en/cloud/paas/goldengate-cloud/tutorial-change-private-key-format/)
```

## 二、使用ssh-keygen

生成密钥，一路回车选择默认选项就好了：

```bash
ssh-keygen -t rsa -b 1024 -f piserver -C "Piserver-ssh-key"
```

配置服务器，将公钥放到服务器上：

```bash
cat piserver.pub >> ~/.ssh/authorized_keys
```

配置连接端：

```bash
vim ~/.ssh/config
```

添加以下内容：

```
Host piserver
     HostName 192.168.137.120
     Port 22
     User pi
     IdentityFile ~/ssh-private-key/piserver
```

