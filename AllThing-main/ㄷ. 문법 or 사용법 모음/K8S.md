1. 초기 구성
	 - winget 을 사용한 kubectl 설치
		 - **winget install -e --id Kubernetes.kubectl**
	- home 디렉토리 내부에 /.kube 디렉토리 생성
	- /.kube 에 config(확장자 없이 또는 확장자 환경변수 지정 후) 파일 생성
	- kubectl ns 로 namespace 목록 확인
	- namespace 목록 떠야 정상 적용


pod(jade-web.yaml), sevice(jade-web-service.yaml) 파일을 
고객사에 가져가서
shell 명령을 통해 ( 해당 파일 실행하고 적용할 수 있는 명령어, 그에 필요한 사전 명령어 순서대로 )
pod, service 를 k8s 서버에 설치
1. 정상 설치 확인
2. nodePort 접근 확인, 화면 정상적으로 뜨는지 확인
