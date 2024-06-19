### 1. EC2 Linux Server Create
===========================================================

* **VPC**
  * **Name = `skills-vpc`**
  * **Ip = `10.0.0.0/16`**
 
===========================================================

* **Subnet**
  * **A Public Name = `skills-public-a`, Ip : `10.0.1.0/24`**
  * **B Public Name = `skills-public-b`, Ip : `10.0.2.0/24`**
  * **A Private Name = `skills-private-a`, Ip : `10.0.3.0/24`**
  * **B Private Name = `skills-private-b`, Ip : `10.0.4.0/24`**
 
===========================================================

* **Route**
  * **A, B Public = `skills-public-rt`**
  * **A Private = `skills-private-rt-a`**
  * **B Private = `skills-private-rt-b`**

===========================================================

* **IGW ( Internet GateWay )**
  * **Name = `skills-igw`**
 
===========================================================

* **NGW ( Nat GateWay )**
  * **A Private Name = `skills-ngw-a`**
  * **B Private Name = `skills-ngw-b`**
 
===========================================================

* **SG ( Security Group )**
  * **In : `22, 2220`**
  * **Out : `All` or `443`**
 
===========================================================

* **EC2**
  * **Name = `skills-bastion`**
  * **Type = `t2.micro`**
  * **OS = `Amazon Linux`**
  * **Region = `ap-northeast-2`**
 
===========================================================
