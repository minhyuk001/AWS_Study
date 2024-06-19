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

* **Checking**
  * **Setting**
    * **1. 리전이 정확한지 확인한다**
    * **2. 서버에 접속할 수 있는지 확인한다**
  * **VPC**
    * **1. VPC 이름이 `skills-vpc`인지 확인한다**
    * **2. VPC IP가 `10.0.0.0/16`인지 확인한다**
  * **Subnet**
    * **1. A Public 이름이 `skills-public-a`인지 확인한다**
    * **1-1. A Public IP가 `10.0.1.0/24`인지 확인한다**
    * **2. B Public 이름이 `skills-public-b`인지 확인한다**
    * **2-2. B Public IP가 `10.0.2.0/24`인지 확인한다**
    * **3. A Private 이름이 `skills-private-a`인지 확인한다**
    * **3-3. A Private IP가 `10.0.3.0/24`인지 확인한다**
    * **4. B Private 이름이 `skills-private-b`인지 확인한다**
    * **4-4. B Private IP가 `10.0.4.0/24`인지 확인한다**
  * **Route**
    * **1. `skills-public-rt`, `skills-private-rt-a`, `skills-private-rt-b`이 생성되어 있는지 확인한다**
    * **2. A, B Public 서브넷이 `skills-public-rt`에 연결되어 있는지 확인한다**
