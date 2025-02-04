
##### .filter((value): value is number => value !== undefined)
- value가 undefined가 아닌 경우에만 리턴되는 배열에 포함
- value is number : 타입 가드, 타입 스크립트에게 value가 number 타입임을 보장하는 코드, 이렇게 하면 타입 스크립트는 이 필터링 후의 배열이 number[]임을 인식할 수 있다.