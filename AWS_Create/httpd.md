### httpd 설치 명령어
```
sudo yum install httpd -y // httpd 설치
sudo systemctl start httpd // httpd 실행
```

### 현재 위치로 S3 버킷 불러오기
```
aws s3 cp [url] .
```
### index.html로 파일이름 변경
```
sudo cp [파일이름] index.html
```
### 파일 위치 이동
```
cd /var/www/html/index.html
```
### httpd 재시작
```
sudo systemctl restart httpd
```
