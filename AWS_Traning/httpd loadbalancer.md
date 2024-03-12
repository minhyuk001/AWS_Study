### Httpd 보안그룹
```
Port : 80
```

### Httpd 설치
```
sudo yum install httpd -y
```

### Httpd 실행
```
sudo systemctl start httpd
```

### Index 생성
```
cat <<EOF >> index.html
```

### Index 이동
```
sudo mv index.html /var/www/html
```

### Httpd 재부팅
```
sudo systemctl restart httpd
```

### Red 파일
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body style="background-color: red;">
    Red
</body>
</html>
```

### Blue 파일
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body style="background-color: blue;">
    Blue
</body>
</html>
```

### Yellow 파일
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body style="background-color: yellow;">
    Yellow
</body>
</html>
```
