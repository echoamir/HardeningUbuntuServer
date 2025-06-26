## Add user 
```
adduser maratus
usermod -aG sudo maratus
usermod -aG www-data maratus
```
```
su - maratus
```
## Add public keys
```
mkdir ~/.ssh
chmod 700 ~/.ssh
touch ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys
chown -R maratus:maratus /home/maratus/.ssh
vim ~/.ssh/authorized_keys
```

## Config sshd file
```
sudo sed -i 's/#\?PermitRootLogin .*/PermitRootLogin no/' /etc/ssh/sshd_config
sudo sed -i 's/#\?Port .*/Port 1999/' /etc/ssh/sshd_config
sudo sed -i 's/#\?PubkeyAuthentication .*/PubkeyAuthentication yes/' /etc/ssh/sshd_config
sudo sed -i 's/#\?PasswordAuthentication .*/PasswordAuthentication no/' /etc/ssh/sshd_config
sudo sed -i 's/#\?AllowAgentForwarding .*/AllowAgentForwarding no/' /etc/ssh/sshd_config
sudo sed -i 's/#\?AllowTcpForwarding .*/AllowTcpForwarding no/' /etc/ssh/sshd_config
sudo sed -i 's/#\?X11Forwarding .*/X11Forwarding no/' /etc/ssh/sshd_config
sudo sed -i 's/#\?PrintMotd .*/PrintMotd no/' /etc/ssh/sshd_config
sudo sed -i 's/#\?TCPKeepAlive .*/TCPKeepAlive no/' /etc/ssh/sshd_config
sudo sed -i 's/#\?Compression .*/Compression no/' /etc/ssh/sshd_config
sudo sed -i 's/#\?ClientAliveCountMax .*/ClientAliveCountMax 2/' /etc/ssh/sshd_config
sudo sed -i 's/#\?UsePAM .*/UsePAM yes/' /etc/ssh/sshd_config
sudo sed -i 's/#\?ChallengeResponseAuthentication .*/ChallengeResponseAuthentication no/' /etc/ssh/sshd_config
sudo sed -i 's/#\?MaxAuthTries .*/MaxAuthTries 3/' /etc/ssh/sshd_config
sudo sed -i 's/#\?MaxSessions .*/MaxSessions 2/' /etc/ssh/sshd_config
sudo sed -i 's/#\?LogLevel .*/LogLevel VERBOSE/' /etc/ssh/sshd_config
sudo sed -i 's/#\?ListenAddress .*/ListenAddress 0.0.0.0/' /etc/ssh/sshd_config
#Banner
```



## Confirm changes
```
grep 'PasswordAuthentication \|Port \|PubkeyAuthentication \|PermitRootLogin \|ListenAddress \|UsePAM \|X11Forwarding \|AllowUsers \|AllowGroups \|LogLevel \|MaxAuthTries \|MaxSessions ' /etc/ssh/sshd_config
```

## Restart SSH service
```
sudo sshd -t
sudo systemctl restart ssh
```
## Install Package
```
sudo apt-get update
sudo apt install bash-completion
sudo apt install -y rsyslog
sudo apt-get install auditd
sudo service auditd start
sudo service auditd status
```
## iptables  
```
sudo apt install iptables-persistent
*filter
-A INPUT -i lo -j ACCEPT
-A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
-A INPUT -p tcp --dport 1999 -j ACCEPT
-A INPUT -p tcp --dport 80 -j ACCEPT
-A INPUT -p tcp --dport 443 -j ACCEPT
-P INPUT DROP
-P FORWARD DROP
-P OUTPUT ACCEPT
COMMIT

```













