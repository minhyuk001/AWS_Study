# AWS Auto Scaling
* GroupMinSize/ GroupMaxSize : Auto Scaling 그룹의 최소/최대 크기

* GroupDesiredCapacity : Auto Scaling 그룹에서 유지 관리를 시도하는 인스턴스의 수

* GroupServiceInstances : Auto Scaling그룹의 일부로 실행되는 인스턴스의 수

* GroupPendingInstances : 아직 실행되지 않은 인스턴스의 수

* GroupStandbtInstances : Standby 상태에 있는 인스턴스의 수

* GroupTerminatingInstances : 종료 중인 인스턴스의 수


# Amazon Ec2
* CPUUtilization : 인스턴스에서 현재 사용 중인 할당된 EC2 컴퓨팅 유닛의 비율

* DiskReadOps : 인스턴스에 사용할 수 있는 스토어 볼륨에서 읽기 성능

* DiskWriteOps : 인스턴스에 사용할 수 있는 스토어 볼륨에서 쓰가 성능

* DiskReadBytes : 인스턴스에 사용할 수 있는 스토어 볼륨에서 읽은 바이트 수

* DiskWriteBytes : 인스턴스에 사용할 수 있는 스토어 볼륨에서 쓴 바이트 수

* NetworkIn : 인스턴스가 네트워크 인터페이스를 통해 받은 바이트 수

* NetworkOut : 인스턴스가 네트워크 인터페이스를 통해 보낸 바이트 수

* NetworkPacketsIn : 인스턴스가 네트워크 인터페이스를 통해 받은 패킷 수

* NetworkPacketsOut : 인스턴스가 네트워크 인터페이스를 통해 보낸 패킷 수


# ELB
* BackendConnectionErros : 로드 밸런서와 등록된 인스턴스 사이에 성공적으로 구성되지 않은 연결 수

* HealthHostCount : 로드 밸런서에 등록된 정상 상태의 인스턴스 수

* HTTPCode_Backend_XXX : 등록된 인스턴스에서 생성된 HTTP 응답 코드 수

* HTTPCode_ELB_4XX : 로드 밸런서에서 생성된 HTTP 4XX 클라이언트 오류 코드 수

* HTTPCode_ELB_5XX : 로드 밸런서에서 생성된 HTTP 5XX 서버 오류 코드 수

* Latency : 로드 밸런서가 등록된 인스턴스에 요청을 보낸 시간부터 인스턴스가 응답 헤더를 보내기 시작할때까지의 총 경과 시간

* RequestsCount : 지정한 주기(1분 또는 5분)에 완료된 요청 또는 연결 수

* SpiloverCount : 서지 대기열이 가득 찼기 때문에 거부된 요청 수

* SugreQueueLength : 정상 인스턴스 대상으로 라우팅이 보류 중인 총 요청 또는 연결 수


# Amazon RDS
* CPUUtilization : CPU 사용 백분율

* DatabaseConnections : 사용 중인 데이터베이스 연결 수

* DiskQueueDepth : 디스크 엑세스를 대기 중인 I/O (읽기/쓰기 요청) 수

* FailedSQLServerAgentJobsCount : 최근 1분간 실패한 SQL Server 에이전트 작업의 수

* NetworkReceiveThroughput : DB 인스턴스 수신 네트워크 트래픽

* NetworkTransmitThroughput : DB 인스턴스 송신 네트워크 트래픽

* ReadIOPS : 초당 평균 디스크 읽기 I/O 연산 수

* ReadLatency : 디스크 I/O 연산당 평균 처리 시간

* ReadThroughput : 초당 디스크에서 읽은 평균 바이트 수

* SwapUsage : DB 인스턴스에서 사용된 스왑 공간 크기

* WriteIOPS : 초당 평균 디스크 쓰기 I/O 연산 수

* WriteLatency : 디스크 I/O 연산당 평균 처리 시간

* WriteThroughput : 초당 디스크에 쓴 평균 바이트 수
