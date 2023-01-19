# Blog-server

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
