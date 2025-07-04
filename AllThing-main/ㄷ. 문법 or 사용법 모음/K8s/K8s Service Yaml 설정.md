``` yaml
apiVersion: v1
kind: Service
metadata:
  name: my-service
  namespace: my-namespace
  labels:
    app: my-app
    tier: backend
  annotations:
    service.beta.kubernetes.io/aws-load-balancer-backend-protocol: http
  finalizers:
    - service.kubernetes.io/load-balancer-cleanup
```

- 위 내용을 적용하면, 클러스터 내부 네임스페이스(위에서는 my-namespace)에 metadata 에 설정한 name 대로 service 가 생성
- 필드 설명
	- **name**: 생성하려는 서비스의 이름 설정
	- **namespace**: 생성하려는 서비스가 속하게 될 네임 스페이스 지정
	- **labels**: key:value, 리소스를 선택하거나 분류, 셀렉터 연동 등에 사용됨
	- **annotation**: key:value, 머신 전용 정보나 임시 설정 등에 사용됨, 리소스 동작에는 영향 없음
	- **finalizers**: 리소스 삭제 전에 반드시 실행되어야 할 클린업 작업 정의. 주로 외부 리소스 해제나 정리에 사용

``` 
my-service.default.svc.cluster.local
```
- 위 yaml을 적용했을 때, my-service 라는 이름의 서비스가 생성된다.
- 이 이름은 클러스터 DNS 이름으로도 사용된다.
	- **default** : 네임 스페이스
	- **svc**: 서비스
	- **cluster.local**: 클러스터 도메인(기본 값)