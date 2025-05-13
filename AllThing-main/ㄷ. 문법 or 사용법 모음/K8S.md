1. 초기 구성
	 - winget 을 사용한 kubectl 설치
		 - **winget install -e --id Kubernetes.kubectl**
	- home 디렉토리 내부에 /.kube 디렉토리 생성
	- /.kube 에 config(확장자 없이 또는 확장자 환경변수 지정 후) 파일 생성
	- kubectl ns 로 namespace 목록 확인
	- namespace 목록 떠야 정상 적용