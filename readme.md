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

### 배포 방법
1. 배포할 client, server의 .env파일의 MODE값이 production인지 확인
2. production일 경우 build
3. client일 경우 package.json을 찹고해 deploy스크립트까지 
