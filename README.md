# ssh-setup
A guide on how to set up your machine for ssh (secure shell). 

## Generate public/private rsa key pair
ssh-keygen  
This command generates the rsa public/private key pair. Note the directory where the key pair is placed for the following steps. 

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
