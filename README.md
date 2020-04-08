# ssh-setup
A guide on how to set up your machine for ssh (secure shell). 

## Generate public/private rsa key pair
ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/ylo/.ssh/id_rsa): mykey
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in mykey.
Your public key has been saved in mykey.pub.
The key fingerprint is:
SHA256:GKW7yzA1J1qkr1Cr9MhUwAbHbF2NrIPEgZXeOUOz3Us ylo@klar
The key's randomart image is:
+---[RSA 2048]----+
|.*++ o.o.        |
|.+B + oo.        |
| +++ *+.         |
| .o.Oo.+E        |
|    ++B.S.       |
|   o * =.        |
|  + = o          |
| + = = .         |
|  + o o          |
+----[SHA256]-----+

## Add ssh config
Edit ~/.ssh/config to add the following lines

Host *
    ServerAliveInterval 300
    ServerAliveCountMax 2
    AddKeysToAgent yes

Host login1
    User username
    Hostname login1.xxx.local
    IdentityFile ~/.ssh/mykey
    LocalForward 21001 localhost:21001
    ForwardX11 yes
    
## Login without password
ssh login1 
