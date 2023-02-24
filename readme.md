# MP-CloudServer

## File Info
 - docker-compose.yml
   - docker-compose config file
 - client.conf
   - React For Nginx virtual host setting
 - server.conf
   - Express For Nginx virtual host setting

## Installation

### Project Setting - first step
```
mv ./docker-compose.yml ../
docker-compose up -d
```

### Server Setting - Last step

```
# NVM
docker exec -it web /bin/sh
apt-get update -y
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.0/install.sh | bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"
nvm install 16.11.0
nvm use 16.11.0
npm install
# pm2
npm install pm2 -g
pm2 start /blog-server/main.js --watch
```

AWS Ubuntu Root password셋팅
```
Please login as the user "ubuntu" rather than the user "root"
```

Docker 셋팅
```
# 엡데이트 
sudo apt update
sudo apt upgrade

# https기반 저장소(repository) 접근하기 위한 도구들 설치
sudo apt install apt-transport-https ca-certificates curl software-properties-common

# key 받아오기
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

# docker 저장소 추가
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

sudo apt install docker-ce

# sudo 없이 docker 실행 준비
sudo usermod -aG docker $USER
```

NVM 셋팅
```
apt-get update -y
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.0/install.sh | bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"
nvm install 16.11.0
nvm use 16.11.0
npm install
```

Docker 이미지 생성
```
docker build . -t blog-server
```

컨테이너 생성 및 실행
```
docker container run --name blog-server -d -p 8000:8000 blog-server
```

crontab에 seo 스크립트 등록
```
0 22 * * * /home/blog-server/seo.sh
```

### 배포 방법
1. 배포할 client, server의 .env파일의 MODE값이 production인지 확인
2. production일 경우 build
3. client일 경우 package.json을 찹고해 deploy스크립트까지 
