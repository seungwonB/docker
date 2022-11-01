# docker
### 1. Why docker
- 웹 앱을 만드려면 운영체제 위에 웹서버나 데이터베이스를 깔아야한다. <br>
- 하지만 과정이 까다롭다. <br>
- 때문에 등장한 게 도커. <br>
### 2. What is docker
- 하나의 컴퓨터에 가상으로 컴퓨터를 만들고 OS를 깔고 웹서버를 설치하면 별도의 컴퓨터는 필요없다.<br>
- 한대의 컴퓨터안에서 각각의 앱을 격리된 환경에서 실행한다.<br>
- 운영체제가 설치된 컴퓨터를 host,<br>
- host에서 실행된 각각의 격리된 환경을 container라고 부른다.<br>
- 도커는 리눅스 운영체제 기술이다.<br>
  - 도커 위에서 돌아가는 컨테이너, 또 그 컨테이너 안에서 돌아가는 앱들은 리눅스 안에서 돌아가는 앱들이다.<br>
  - 리눅스 OS가 아니면, 가상머신을 깔고 그 가상머신에 리눅스 운영체제를 깔면 거기서 컨테이너 기술을 사용할 수 있다.<br>
### 3. How
- hub.docker.com 에서 필요한 소스를 받으면 된다.<br>
- 이곳에서 찾은 것을 image라고 한다.<br>
- 이미지를 실행하는 것을 container라고 한다.<br>
- 이미지도 여러 개의 컨테이너를 가질 수 있다.<br>
- 이미지를 다운 받는 행위를 pull, 실행을 run이라 한다.<br>
### 4. Command (httpd 편)
- docker run [image name] : 실행<br>
- docker ps : 현재 실행 중인 상황<br>
- docker ps -a : 전체 상황<br>
- docker run --name [container name] [image name] : 이름을 붙여 실행<br>
- docker logs -f [container name] : 로그의 변화 실시간으로 <br>
- docker stop [container name] : 중단
- docker rm [container name] : 컨테이너 지우기(중단 후)<br>
- docker rm --force [container name] : 중단 없이 지우기<br>
- docker rmi [image name] : 이미지 삭제<br>
- docker run --name [container name] -p 8080:80 [image name] : 포트까지 지정하여 실행<br>
- docker exec it [container name] /bin/bash : 컨테이너의 쉘로 들어가 명령어 실행. (exit로 나감)<br>
   - cd /usr/local/apache2/htdocs<br>
   - apt update<br>
   - apt install nano<br>
   - nano index.html<br> : 이곳에서 html 수정 가능 but 컨테이너가 사라질 때 위험함.<br>
- docker run -p 8080:80 -v 절대경로:/usr/local/apache2/htdocs httpd : 호스트에서 html 수정 가능

# docker-compose
### 1. What
- 도커 실행하는 명령어가 너무 길다.
- 때문에 docker-compose.yml이라는 파일을 만들고 그곳에 명령어를 입력한다.
- docker-compose up 명령어 한 줄로 컨테이너가 만들어진다.
### 2. How 
- 예를 들어 다음과 같은 도커 실행문이 있다고 치자.<br>
![image](https://user-images.githubusercontent.com/73030613/199261710-c575dab8-281d-487c-b758-54da04618c7e.png) <br>
- yml 파일을 만들어 실행문을 넣어놓는다. <br>
![image](https://user-images.githubusercontent.com/73030613/199262137-4bc27aad-4ab8-47a0-af7f-3bf53081113a.png)<br>
- 그렇게 되면 docker-compose up 명령어 한 줄로 실행이 가능하다.
