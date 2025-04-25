#### 문제점
1. Portal 에서 인증 정보를 Session Storage 로 받고 있음
2. 화면 클라이언트의 상태는 휘발성이기 때문에 (axios header 또한) 항상 인증 정보를 보관하고 있을 방법이 필요함
3. Session, Local Storage 혹은 Cookie 중 하나 인데,
4. 백엔드에서 HttpOnly Cookie 를 생성해야 한다.
5. 현재는 Portal, Backend 모두 Cookie 생성하지 않으려 하고 있고, 이미 진행된 사항도 그렇게 수정하기에는 쉽지 않은 상황
6. 인증 정보를 계속 가지고 인증 파악을 하려면 Session에 인증 정보를 가지고 있어야 하는 상태