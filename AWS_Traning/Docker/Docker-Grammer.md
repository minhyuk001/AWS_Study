```Dockerfile
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
