
## EC2 사용자 데이터베이스 소스

### Linux
```java
#!/bin/bash
echo 'Port (포트 번호)' >> /etc/ssh/sshd_config
systemctl restart sshd
sed -i "s/PasswordAuthentication no/PasswordAuthentication yes/g" /etc/ssh/sshd_config
echo "<AMI 이름>:<비밀번호>" | chpasswd
systemctl restart sshd
```

### ubuntu
```java
#!/bin/bash
apt update -y
apt install curl jq -y
sed -i "s/PasswordAuthentication no/PasswordAuthentication yes/g" /etc/ssh/sshd_config
echo -e "<비밀번호>**\n<비밀번호>**" | passwd ubuntu
echo "Port (포트 번호)" >> /etc/ssh/sshd_config
systemctl restart sshd
```

## CMD 연결
```
ssh ec2-user@(ip) -p (포트)
```
