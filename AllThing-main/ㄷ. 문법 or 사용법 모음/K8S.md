1. 초기 구성
	 - winget 을 사용한 kubectl 설치
		 - **winget install -e --id Kubernetes.kubectl**
	- home 디렉토리 내부에 /.kube 디렉토리 생성
	- /.kube 에 config(확장자 없이 또는 확장자 환경변수 지정 후) 파일 생성
	- kubectl ns 로 namespace 목록 확인
	- namespace 목록 떠야 정상 적용



#### 실제 설치 방식
pod(jade-web.yaml), sevice(jade-web-service.yaml) 파일을 
고객사에 가져가서
shell 명령을 통해 ( 해당 파일 실행하고 적용할 수 있는 명령어, 그에 필요한 사전 명령어 순서대로 )
pod, service 를 k8s 서버에 설치
1. 정상 설치 확인
2. nodePort 접근 확인, 화면 정상적으로 뜨는지 확인

### alias 설정
- window 의 경우, $PROFILE 내부에 alias 설정을 통해 alias 를 사용할 수 있는데,
- notepad $PROFILE 로 해당 파일에 설정이 적용되어 있는지 확인할 수 있다.
- 만약 해당 파일이 없다면,
	- New-Item -ItemType File -Path $PROFILE -Force
- 중간 파일이 없을 수도 있기 때문에 디렉토리도 먼저 만들어주는게 더 안전할 수 있다.
- 만약, 이 시스템에서 스크립트를 실행할 수 없으므로 ...ps1 파일을 로드할 수 없습니다. 에러가 발생하는 경우,
	- 파워쉘의 실행 정책 때문에 스크립트가 실행되지 않는 것이며
	- Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
	- 을 통해 현재 접속자에 대해서만 실행 정책을 완화하는 명령을 사용할 수 있다.
		- - `RemoteSigned`: 로컬에서 만든 스크립트는 실행 가능, 인터넷에서 받은 건 서명 필요
		- `-Scope CurrentUser`: 현재 사용자에게만 적용되므로 시스템 전체에 영향 없음
- 모든 설정이 완료 되어 $PROFILE 을 열어볼 수 있다면,
	- 해당 파일 내에
		- function k { kubectl $args }
		- Set-Alias kgp 'kubectl get pods'
		- Set-Alias kaf 'kubectl apply -f'
	- 위와 같은 명령을 저장해 alias 설정을 추가할 수 있다.