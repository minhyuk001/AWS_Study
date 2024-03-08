### Terraform file name
* Provider = 0-Provider
* VPC = 1-VPC

### Terraform Setting
```tf
terraform init
```

### Terraform Start
```tf
terraform apply
```

### Terraform Remove
```tf
terraform destroy
```

### Provider Terraform
```tf
provider "aws" {
  access_key = ""
  secret_key = ""
  region = "ap-northeast-2"
  profile = "default"
}
```


### VPC terraform
```tf
# 환경변수 정의
variable "Vpc_Content" {
  default = {
    default_name       = "skills"
    vpc_name           = "skills-vpc"
    vpc_cidr           = "10.0.0.0/16"
    public_subnet_name = ["skills-pub-a", "skills-pub-b", "skills-pub-c"]
    public_cidr        = ["10.0.1.0/24", "10.0.2.0/24", "10.0.3.0/24"]
    private_subnet_name = ["skills-priv-a", "skills-priv-b", "skills-priv-c"]
    private_cidr        = ["10.0.4.0/24", "10.0.5.0/24", "10.0.6.0/24"]
  }
}

# VPC 생성
resource "aws_vpc" "skills_vpc" {
  cidr_block           = var.Vpc_Content.vpc_cidr
  enable_dns_hostnames = true
  enable_dns_support   = true
  tags                 = { Name = var.Vpc_Content.vpc_name }
}

# 퍼블릭 서브넷 생성
resource "aws_subnet" "public" {
  count                  = 3
  vpc_id                 = aws_vpc.skills_vpc.id
  cidr_block             = var.Vpc_Content.public_cidr[count.index]
  availability_zone      = "ap-northeast-2${element(["a", "b", "c"], count.index)}"
  map_public_ip_on_launch = true

  tags = {
    Name = var.Vpc_Content.public_subnet_name[count.index]
  }
}

# 프라이빗 서브넷 생성
resource "aws_subnet" "private" {
  count             = 3
  vpc_id            = aws_vpc.skills_vpc.id
  cidr_block        = var.Vpc_Content.private_cidr[count.index]
  availability_zone = "ap-northeast-2${element(["a", "b", "c"], count.index)}"

  tags = {
    Name = var.Vpc_Content.private_subnet_name[count.index]
  }
}

# Elastic IP 생성
resource "aws_eip" "nat" {
  count  = 3
  domain = "vpc"
}

# NAT 게이트웨이 생성
resource "aws_nat_gateway" "nat" {
  count         = 3
  allocation_id = aws_eip.nat[count.index].id
  subnet_id     = aws_subnet.public[count.index].id

  tags = {
    Name = "nat-${element(["a", "b", "c"], count.index)}"
  }
}

# 인터넷 게이트웨이 생성
resource "aws_internet_gateway" "internet_gateway" {
  vpc_id = aws_vpc.skills_vpc.id
  tags = {
    Name = "igw"
  }
}

# 퍼블릭 라우팅 테이블 생성
resource "aws_route_table" "public" {
  vpc_id = aws_vpc.skills_vpc.id

  route {
    cidr_block = "0.0.0.0/0"
    gateway_id = aws_internet_gateway.internet_gateway.id
  }

  tags = {
    Name = "skills-pub-rt"
  }
}

# 프라이빗 라우팅 테이블 생성
resource "aws_route_table" "private" {
  count  = 3
  vpc_id = aws_vpc.skills_vpc.id

  tags = {
    Name = "${var.Vpc_Content.private_subnet_name[count.index]}-rt"
  }
}

# 프라이빗 라우팅 테이블에 NAT 게이트웨이를 추가
resource "aws_route" "nat_gateway_route" {
  count             = 3
  route_table_id    = aws_route_table.private[count.index].id
  destination_cidr_block = "0.0.0.0/0"
  nat_gateway_id    = aws_nat_gateway.nat[count.index].id
}


# 퍼블릭 서브넷과 연결된 라우팅 테이블을 지정
resource "aws_route_table_association" "public" {
  count             = 3
  subnet_id         = aws_subnet.public[count.index].id
  route_table_id    = aws_route_table.public.id
}

# 프라이빗 서브넷과 연결된 라우팅 테이블을 지정
resource "aws_route_table_association" "private" {
  count             = 3
  subnet_id         = aws_subnet.private[count.index].id
  route_table_id    = aws_route_table.private[count.index].id
}
```

### EC2 instance Terraform
```tf
resource "aws_instance" "skills_ec2" {
  ami           = var.Ec2_Content.instance_ami
  instance_type = var.Ec2_Content.instance_type
  subnet_id     = aws_subnet.public[0].id
  vpc_security_group_ids = [aws_security_group.skills_security_group.id]
  user_data = <<-EOF
    #!/bin/bash
    echo 'Port 2220' >> /etc/ssh/sshd_config
    systemctl restart sshd
    sed -i "s/PasswordAuthentication no/PasswordAuthentication yes/g" /etc/ssh/sshd_config
    sudo echo -e "1234\n1234" | sudo passwd ec2-user
    systemctl restart sshd
  EOF
  # 사용자 데이터 설정
  tags = { Name = var.Ec2_Content.instance_name }
}
```
