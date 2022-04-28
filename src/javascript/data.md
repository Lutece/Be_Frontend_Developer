# 자료형

- Boolean : 논리적 값 (true, false)
- null : 존재하지 않거나 유효하지 않은 주소 표시
- undefined : 선언 후 값을 할당하지 않은 변수
- number : 정수, 실수 등의 숫자
- string : 빈 문자열이나 글자들을 표현하는 문자열
- symbol : 문자열과 함께 객체 property로 사용, ES6에 추가
- object : 두개 이상의 복잡한 개체 저장 가능

## 원시 타입

- Booelan, null, undefined, number, string, symbol
  - null : null은 값이 비어 있다는 의미로 표현되는 자료형
    - 존재하지 않는, 비어있는, 알 수 없는 값을 나타내는 데 사용
  - undefined : 값이 할당되어 있지 않은 상태를 나타낼 때 사용되는 자료형
  - number: infinity, -infinity, NaN 같은 특수 숫자 값이 포함되어 있다.

## 객체 타입

- object : 다수의 원시 자료형을 포함하거나 복잡한 개체를 표현할 수 있는 자료형

### 객체 복사의 문제점

- Shallow Copy vs Deep Copy
  - Shallow Copy : Object.assing({}, object), for, spread operator, {...object}
  - Deep Copy

```js
Copy Object (그림과 함께 이해하기)

function copyObj(obj) {
  let result = {};

  for(let key in obj) {
    if(typeof obj[key] === "object") result[key] = copyObj(obj[key]);
    else result[key] = obj[key];
  }

  return result;
}
```

```js
JSON;

JSON.parse(JSON.stringify(object));
```
