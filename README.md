# 自用版sub-web
## 使用方法：
docker build -t subweb:latest .
docker run -d -p 58080:80 --restart always --name subweb subweb-local:latest
