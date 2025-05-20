## SSO 방식
- Single Sign On
- 1회 사용자 인증으로 다수 애플리케이션 및 웹사이트에 대한 사용자 로그인 허용 로그인 방식

## 현재 프로젝트 인증 구성
![[Pasted image 20250520120310.png]]

### 기존 방식
1. Portal 에서 로그인
2. BMP 이동 버튼 클릭
3. BMP 메인 이동 전 SSO 페이지 생성
	1. 해당 페이지에서 BMP 메인 페이지로 이동할 때, 인증 정보를 받기 위한 Nginx 설정이 기존과 큰 차이가 있음
	2. 기존에는 통합되어 있던 location, upstream 옵션을 분리하고, 해당하는 디렉토리를 각각 생성해 location, upstream 별 따로 저장
	3. 