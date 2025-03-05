#### computed 를 사용해 선언한 변수가 내부에 들어가 있는 값이 변경됨에도 computed 반응하지 않는 문제 발생

#### ! computed 가 반응하는 시기
1. computed 내부에서 사용된 ref 로 선언된 변수의 .value가 변경될 때,
2. computed 내부에서 사용된 reactive로 생성된 객체의 속성 값이 변경될 때,
3. computed 내부에서 사용된 다른 computed 속성의 값이 변경될 때
위 세 경우에 computed 속성이 재 계산된다.



