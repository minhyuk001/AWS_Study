* 우분투 인스턴트 사용자 데이터 베이스
```
#!/bin/bash
apt update -y
apt install curl jq -y
sed -i "s/PasswordAuthentication no/PasswordAuthentication yes/g" /etc/ssh/sshd_config
echo -e "Skills2024**\nSkills2024**" | passwd ubuntu
echo "Port 2220" >> /etc/ssh/sshd_config
systemctl restart sshd
```
