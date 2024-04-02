### IAM 사용자 생성  및 CodeCommit 사용권한 추가
```
CodeCommit을 사용할 수 있는 권한을 가진 사용자 생성하기
IAM > 사용자 > "사용자 추가"
```

### IAM 사용자  AWS CodeCommit에 대한 HTTPS Git 자격증명 생성
```
1. AWS Management Console에 로그인하여 https://console.aws.amazon.com/iam/에서 IAM 콘솔을 연다.
CodeCommit에 대한 연결에 Git 자격 증명을 생성하고 사용할 IAM 사용자로 로그인한다.
```
```
2. CodeCommit 사용을 원하는 계정으로 IAM에 접속해서 사용자> '보안 자격 증명'탭을 클릭 후 "자격 증명 생성" 버튼을 클릭.
```
```
3. 이제 이 사용자 ID와 패스워드를 이용해 CodeCommit Repository에 접속 함.
```

### CodeCommit Repository 생성
```
AWS Console 상에서 개발자 도구 > CodeCommit > 리포지토리 > 리포지토리를 클릭해서 새로운 리포지토리를 생성하도록 함.
```

### HTTPS를 통한 레파지토리 연결
```
방금생성한 레파지토리에 연결을 위한 URL을 복사,
개발자도구 > CodeCommit > 리포지토리를 클릭해 생성한 레파지토리의 왼쪽에 있는 URL 복제 탭에서 HTTPS를 클릭하도록 한다.
```

### EC2에 git 업로드
```
git clone <URL>
```

### branch 생성
```
git branch -M <Name>
```

### 현재 경로 업데이트
```
git add .
```

### 업데이트 내용
```
git commit -m "<Name>"
```

### git 업로드
```
git push origin <Name>
```

### S3에 정적 컨텐츠 서비스를 위한 버킷(bucket) 만들기 및 정적 컨텐츠 서비스 설정
```
1. AWS콘솔 > Amazon S3 > 버킷 > 버킷 만들기
액세스 차단의 경우 "모든 퍼블릭 액세스 차단" 버튼을 해제함.
```
```
2. AWS웹콘솔> Amazon S3 > 버킷 > [본인이 위에서 만든 버킷명] > 속성
> 정적 웹 사이트 호스팅 > 편집 > 정적 웹사이트 호스팅 활성화 체크
```

### AWS CodePipeline을 이용한 파이프라인 생성
```
1. AWS 콘솔 > 개발자 도구 > CodePipeline > 파이프라인 > 파이프라인 생성 클릭
```
```
2.  소스 공급자로 AWS CodeCommit을 선택하고 리포지토리 이름 항목에서 위에서 만든 CodeCommit의 Repoistory를 선택
```
```
3. 브랜치 이름은 로컬PC의 git에서 만든 배포를 원하는 브랜치명을 선택
```
```
4. 빌드 스테이지 건너뛰기
```
```
5. 배포 스테이지 추가 단계에서 배포 공급자로 'Amazon S3'를 선택하고 리전과 버킷을 선택 ( 압축풀기 체크 )
```
```
6. 생성
```

### 인터넷 브라우저를 통한 접속 테스트
```
1. AWS콘솔 > Amazon S3 > 버킷 > [위에서 만든 버킷명]
```
```
2. 맨 아래로 내려가서 '버킷 웹 사이트 엔드포인트'라는 URL 클릭
```
