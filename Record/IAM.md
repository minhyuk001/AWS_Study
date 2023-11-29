# Identity Access Management ( IAM )

## IAM 이란?
* AWS IAM을 사용하면 AWS 서비스와 리소스에 대한 액세스를 안전하게 관리할 수 있습니다
* AWS 사용자 및 그룹을 만들고 관리하며 AWS 리소스에 대한 액세스를 허용 및 거부할 수 있습니다

### AWS 어카운트 관리 및 리소스/유저/서비스의 권한 제어
* 임시 권한 부여
* 서비스 사용을 위한 인증 정보 부여

### 유저의 생성 및 관리 및 계정의 보안
* Multi-factor Authentication
* 유저의 패스워드 정책 관리

### 다른 계정과의 리소스 공유
### Identity Federation ( Facebook 로그인, 구글 로그인 등 )

## IAM의 구성
> 유저 : 실제 AWS 서비스를 사용하는 사람
* Access Key/Secret Access Key : 유저가 AWS의 서비스를 사용하기 위한 인증 정보
* 유저명/패스워드 : 유저가 AWS 콘솔을 사용하기 위한 인증정보

> 그룹 : 유저의 집합 ( 그룹에 속한 유저는 그룹에 부여된 권한을 행사할 수 있다 )

> 정책 ( Policy ) : JSON 형식으로 정의되며 유저와 그룹, 자격이 무엇을 할 수 있는지에 관한 문서

> 자격 ( Role ) : AWS 리소스에 부여하여 AWS 리소스가 무엇을 할 수 있는지를 정의
* 다른 자격에 대해서 신뢰관계를 구축 가능
* 역할을 바꾸어 가며 서비스를 사용 가능

## IAM 팁
> IAM은 글로벌 서비스 ( -> Region별 서비스가 아님 )
* STS ( Session Token Service )의 경우 Region 별 활성/비활성 처리 가능

> 계정에 별명 부여 가능 -> 로그인 주소 생성 가능

> 유저의 경우 루트 유저와 생성된 유저로 구분
* 루트 유저의 경우 보안에 신경쓰기 ( Multi-factor Authentication 등 )

> 유저의 패스워드 보안 정책 변경 가능 ( 일정 시간마다 패스워드 변경 등 )

> 최소한의 권한만을 허용하는 습관을 들이기 ( Principle of least privilege )
