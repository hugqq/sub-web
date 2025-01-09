# sub-web
## 简介

自用魔改肥羊版，去除广告，增加自用订阅

## 使用方法
```bash
git clone https://github.com/hugqq/sub-web.git

cd sub-web/

docker build -t subweb:latest .

docker run -d -p 58080:80 --restart always --name subweb subweb:latest
```
