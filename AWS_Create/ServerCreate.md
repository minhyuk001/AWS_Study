# AWS EC2 VPC를 사용하여 서버 구축

## VPC
* VPC 생성 ( 구축 )
* Subnet 생성 ( 연결주소 )
* Route 생성 ( 가용영역 )
* Internet Gateway 생성 ( 인터넷 게이트웨이 )
* NAT Gateway 생성 ( 프라이빗 서버 )
<br/>

* cloud-a, cloud-b 등으로 서브넷 정의
* Route는 cloud-rt, cloud-rt-p로 구분
* Subnet과 Route 연결
* Internet Gateway VPC 연결
* NAT Gateway 비공개 cloud-rt-p 연결

## EC2
* 인스턴드 생성
* 보안그룹 생성

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
echo -e "Skills2024**\nSkills2024**" | passwd ubuntu
echo "Port 2220" >> /etc/ssh/sshd_config
systemctl restart sshd
```

## CMD 연결
```
ssh ec2-user@(ip) -p (포트)
```
