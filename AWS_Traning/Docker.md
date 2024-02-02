### Docker Install Command

```
sudo yum install docker -y
sudo usermod -aG docker <AMI Name>
sudo systemctl enable --now docker
sudo chmod 666 /var/run/docker.sock
```


### Docker Grammer
```
FROM <사용할 언어>:<버전>
// FROM ubuntu:latest

RUN <실행할 코드>
// RUN apt install curl -y

USER <파일이름>
// USER match

COPY <파일 이름> .
// COPY app.py .

EXPOSE <포트 번호>
// EXPOSE 8080

WORKDIR  <작업을 할 폴더 이름> 
// 폴더를 도커파일 내에서 생성하고 작업을 폴더안에서 하도록 설정해줍니다.

CMD ["실행할 명령어"]
// CMD ["python", "./app.py"]
// CMD ["./app"]
```

### Docker Add Grammer
```
# 파일 권한 부여
RUN chmod 777 ./<파일 이름>

# 사용자 생성
RUN adduser <사용자 이름>
USER <사용자 이름>
```

## Docker Command

### Docker File 빌드하기
```
docker build --tag <이미지 이름> .
```
 
### Docker Image 실행하기
```
docker run -d -p<더미 포트>:<앱의 포트번호> <이미지 이름>
```

### Docker 이미지 목록 확인하기
```
docker images
```
 
### Docker에서 실행중인 컨테이너 목록 확인하기
```
docker ps
```


### Docker 이미지 삭제하기
```
docker rmi -f <docker images id>
```

### Docker 실행중인 컨테이너 삭제하기
```
docker kill <docker container id>
```

### Localhost 실행확인
```
curl localhost:8080/health
```
```
