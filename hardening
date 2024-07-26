adduser deployer
usermod -aG sudo deployer
usermod -aG www-data deployer

su - deployer

mkdir ~/.ssh
chmod 700 ~/.ssh
touch ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys
chown -R deployer:deployer /home/deployer/.ssh
vim ~/.ssh/authorized_keys

sudo sed -i 's/#\?PermitRootLogin .*/PermitRootLogin no/' /etc/ssh/sshd_config
sudo sed -i 's/#\?Port .*/Port 2222/' /etc/ssh/sshd_config
sudo sed -i 's/#\?PubkeyAuthentication .*/PubkeyAuthentication yes/' /etc/ssh/sshd_config
sudo sed -i 's/#\?PasswordAuthentication .*/PasswordAuthentication no/' /etc/ssh/sshd_config
sudo sed -i 's/#\?AllowAgentForwarding .*/AllowAgentForwarding no/' /etc/ssh/sshd_config
sudo sed -i 's/#\?AllowTcpForwarding .*/AllowTcpForwarding no/' /etc/ssh/sshd_config
sudo sed -i 's/#\?X11Forwarding .*/X11Forwarding no/' /etc/ssh/sshd_config
sudo sed -i 's/#\?PrintMotd .*/PrintMotd no/' /etc/ssh/sshd_config
sudo sed -i 's/#\?TCPKeepAlive .*/TCPKeepAlive no/' /etc/ssh/sshd_config
sudo sed -i 's/#\?Compression .*/Compression no/' /etc/ssh/sshd_config
sudo sed -i 's/#\?ClientAliveCountMax .*/ClientAliveCountMax 2/' /etc/ssh/sshd_config
sudo sed -i 's/#\?AllowUsers .*/AllowUsers deployer/' /etc/ssh/sshd_config
sudo sed -i 's/#\?AllowGroups .*/AllowGroups deployer/' /etc/ssh/sshd_config
sudo sed -i 's/#\?UsePAM .*/UsePAM yes/' /etc/ssh/sshd_config
sudo sed -i 's/#\?ChallengeResponseAuthentication .*/ChallengeResponseAuthentication no/' /etc/ssh/sshd_config
sudo sed -i 's/#\?MaxAuthTries .*/MaxAuthTries 3/' /etc/ssh/sshd_config
sudo sed -i 's/#\?MaxSessions .*/MaxSessions 2/' /etc/ssh/sshd_config
sudo sed -i 's/#\?LogLevel .*/LogLevel VERBSOE/' /etc/ssh/sshd_config
sudo sed -i 's/#\?ListenAddress .*/ListenAddress 0.0.0.0/' /etc/ssh/sshd_config
sudo sed -i 's/#\?PermitRootLogin .*/PermitRootLogin no/' /etc/ssh/sshd_config
sudo sed -i 's/#\?PermitRootLogin .*/PermitRootLogin no/' /etc/ssh/sshd_config
#Banner

sodo apt-get update
sudo apt install bash-completion
#audit
sudo apt-get install auditd
service status auditd
auditd start
auditd restart
















