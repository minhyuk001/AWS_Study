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
