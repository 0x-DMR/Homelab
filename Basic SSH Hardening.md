# SSH Basic Hardening
***
The following is a guide which walks through basic ssh hardening methods that can be done on a linux server or host. This guide includes removing password based authentication for ssh connections, moving the ssh port to a non-standard port as well as creating ssh keys. 

## 1. Generate SSH Key on Host Machine

```
ssh-keygen
```

Save these files to *.ssh*

## 2. SSH onto Machine and Copy Over the Public Key

```
nano .ssh/authorized_keys
```

Cat out the public key from host machine and copy and paste this into the file shown above located in.

## 3. Edit the SSH Config on Linux Box

```
sudo nano /etc/ssh/sshd_config
```

From here change the parameters in the config file to suit your needs. Below are some examples that can be performed:
	Port 22 -> Port 2222
	PubkeyAuthentication no -> PubkeyAuthentication yes
	PasswordAuthentication yes -> PasswordAuthentication No

## 4.  Restart SSH on Box

```
sudo systemctl restart sshd
```

## 5. Exit from Box and Relogin

```
ssh -l <username> <ip-address> -p 2222 -i .ssh/<name of ssh key> 
```

