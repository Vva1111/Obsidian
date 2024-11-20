- **docker --help** : docker 명령어 도움
- **docker ps** : docker container 목록 확인
- **docker images** : docker image 목록 확인
- **docker images | grep node** : 이미지 이름이 node인 docker image만 확인
- **docker logs -f -n {나타낼 log 수} {container id}** : 해당하는 컨테이너 id의 로그 확인
	- -f : follow, 로그 출력이 실시간으로 계속 이어서 표시됨, 새로운 로그 발생 시 즉시 콘솔에 출력
	- -n : 이후에 선언한 숫자 만큼의 log 표현
- **docker network ls** : network 목록 표시
- **docker network inspect {network 이름}** : 해당하는 네트워크 정보 파악
- **docker build -t {이미지 이름}:{태그} {Dockerfile 위치 or . }** .
	- docker 이미지를 빌드하는 명령어
	- -t : 해당 이미지에 이름을 주기 위한 명령어
	-  . : 현재 디렉토리에 있는 Dockerfile을 사용한다는 의미
	- 사용하기 위한 Dockerfile의 위치는 설정 가능
	- 위 명령어로 이미지가 생성되면, ci.yml 파일에서 생성된 이미지를 지정해서 빌드-배포 과정에서 사용할 수 있다
- **docker rm** : 한 개 이상의 컨테이너 삭제
- **docker rmi** : 한 개 이상의 이미지 삭제
	- **docker rmi $(docker images | grep <image_name> | awk '{print $3}')** : 이미지 이름에 해당하는 이미지만 삭제
		- **awk '{print $3}'** :  각 행의 3번째 열(이미지 id)을 추출
- **docker diff** : 컨테이너 파일시스템 내의 파일 혹은 디렉터리의 변경사항 확인
- **docker container 삭제** : 
	1. **docker ps -a** : 도커 컨테이너 목록 확인
	2. docker stop {컨테이너 이름 또는 아이디}
	3. docker rm {컨테이너 이름 또는 아이디}
	- docker rmi {이미지 아이디}
- **docker exec -it {컨테이너 이름 또는 id} bash
	- 컨테이너 내부에 설치되어 있는 이미지의 경우, 호스트 시스템에서 직접 해당 이미지의 명령어를 실행할 수 없기 때문에 컨테이너 내부로 진입해 명령어를 실행해야 한다. 
	- 그 때 해당하는 컨테이너 내부로 진입해 bash를 사용하기 위한 명령어