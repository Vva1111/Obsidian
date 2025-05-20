## 기존 방식
### SPA(프론트 엔드 화면) 프로젝트
1. Jade, Davis 와 같이 SPA 프로젝트는 CICD 과정에서 패키지 build
2. 생성된 build 결과물을 러너 임시 컨테이너 내부의 특정 디렉토리로 옮김 ( cp )
3. 기존에 gitlab-runner 컨테이너 내부 config.toml 설정에 2의 빌드 결과물을 host 로 가지고 올 수 있는 볼륨 설정 ( /data:/data )
4. 이 과정에서 생성된 Build 결과물들이 host 의 특정 디렉토리에 위치할 수 있게 됨

### Integrate(프론트 엔드 프로젝트 - Nginx 통합) 프로젝트
1. Dockerfile 을 사용한 Nginx 이미지 빌드
2. 빌드 된 이미지 저장소에 push
3. 
