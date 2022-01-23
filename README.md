# docker-elk-stack
## 개요
해당 프로젝트는 ELK Stack을 사용해서 로그분석 시스템을 구축할 목적으로 시작되었고,  
이 과정속에서 사용한 docker의 설정파일을 공유해서 다른 사람들의 시간을 절약해주기 위해 작성되었습니다. 

## 목차
1. 시작하기전 검토해봐야 할 사항
    * [환경](#환경)
    * [git 설치](#git-설치)
    * [docker와 docker compose 설치](#docker와-docker-compose-설치)
3. 
4. 


## 시작하기전 검토해봐야 할 사항

### 환경
이 프로젝트는 다음과 같은 환경과 목적?으로 설치되는 것을 전재로 하기 때문에,   
각자의 환경과 목적에 맞게 수정할 필요가 있습니다.  
* 동일한 서버에서 모든 container 실행
* elasticsearch는 1개만 사용(다중노드 구성 X)
* 각 container의 환경설정을 모아서 관리 및 저장(github)

---------------

### git 설치
git clone으로 설치할 서버에 프로젝트를 복사해야 하기 때문에 필요합니다.

*주의할점\* : 해당 내용은 2022/01/23을 기준으로 작성됨
따라서 미래 시점에서는 틀릴수 있기 때문에, 공식 링크를 참고할것*  
[git 공식설치링크>>>>](https://git-scm.com/book/ko/v2/%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-Git-%EC%84%A4%EC%B9%98)
``` Bash
#git 설치
sudo apt install git-all
```

---------------

### docker와 docker compose 설치
각 컨테이너를 실행 및 관리하기 위해 docker를 설치하고,  
한번에 복수의 컨테이너를 관리하기 위해 docker compose를 사용합니다.  
*주의할점\* : 해당 내용은 2022/01/23을 기준으로 작성됨
따라서 미래 시점에서는 틀릴수 있기 때문에, 공식 링크를 참고할것*  
[docker 공식설치링크>>>>](https://docs.docker.com/engine/install/ubuntu/)
[docker compose 공식설치링크>>>>](https://docs.docker.com/compose/install/)


#### docker 설치
``` Bash
#curl이 없을 경우 설치해준다.
sudo apt-get curl

#도커에서 제공하는 스크립트로 도커 최신 버전 설치를 진행
curl -s https://get.docker.com | sudo sh

##제대로 도커를 설치했는지 확인 
#1 도커 버전 확인
docker -v

#2 설치한 패키지 중에 docker가 있는지 확인해보기
dpkg --get-selections | grep docker

#결과2
#docker-ce                                       install
#docker-ce-cli                                   install
```
#### docker compose 설치
``` Bash
#curl이 없을 경우 설치한다.
sudo apt-get curl

# 1. Docker Compose의 현재 안정적인 릴리스를 다운로드합니다.
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

# 2. 바이너리에 실행 권한 적용
sudo chmod +x /usr/local/bin/docker-compose

# 3. 심볼릭 링크 생성
sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose

# 4. 설치 완료 테스트
docker-compose --version
#예) docker-compose version 1.29.2, build 5becea4c

```
