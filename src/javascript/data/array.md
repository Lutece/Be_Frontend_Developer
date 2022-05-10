# Array

## 배열의 실체

- 자바스크립트 배열은 다른 언어에서 말하는 일반적인 배열이 아닌 hash 기반의 개체
- 메모리가 연속적인 밀집 배열(dense array)가 아닌 비 연속적인 희소 배열(sparse array)
- 배열도 iterable 하다 ( for of, for in 사용가능 )

### delete

- delete로 삭제 시 값은 없어지지만 공간은 남게 된다.

### Array.sort

- 배열의 원소는 String으로 치환되어 숫자의 비교의 경우 콜백함수를 통해 정렬 기준을 잡아주어야 한다.

## N차원 Array
- 배열(Array) 안에 N개 만큼의 배열이 존재하는 객체
- 2/3차원 지도 정보, RGB를 저장하는 2차원 사진 파일 등을 표현할 때 활용 가능