# 반복문

## for 반복문

- 선언문(Init Expression), 조건문(Test Expression), 증감문(Update Expression) 형태로 이루어진 반복문
- 조건문이 fail이 되기 전까지 코드 블록을 계속적으로 반복 수행
- 선언문, 조건문, 증감문 자리에 공백 입력 가능

```js

for(IE; TE; UE) {
  Statement Block...
}

/* TE 조건에 맞지 않으면 코드 자체는 수행되지 않는다. */

```

## 반복문 for (확장)

### for ...in 반복문

- 객체의 key, value 형태를 반복하여 수행하는데 최적화된 유형
- 첫번째부터 마지막까지, 객체의 키 개수만큼 반복
  
```js

for (key in object) {
  //code block to be executed
}

```

### for ...of 반복문

- Collection 객체 자체가 Symbol.iterator 속성(property)을 가지고 있어야 동작 가능한 유형
- ES6에 새로 추가된 Collection 기반의 반복 구문

```js

for (variable of iterable) {
  // code block to be executed
}

```

## while 반복문

- 반복문이 참일 때 코드 블록을 계속해서 반복 수행하는 반복문
- for 문에 비해 선언문과 증감문 없이 loop를 수행하며, 무한 loop 등 수행 시 많이 사용
- 조건문을 코드 블럭보다 아래로 옮긴 do ... while 반복문도 존재 
  ( 조건문과 상관없이 최소 한번 수행이 필요할 때 많이 사용 )

```js

while (Test Expression) {
  Statement Block
}

do {
  Statement BLock
} while (Test Expression)

```

## 반복문 제어

### break

- 반복문 수행 시 코드 블록을 탈출할 때 사용되는 식별자
- 다중 반복문일 경우 가장 안쪽의 반복문을 종료
- Label을 통하여 다중 반복문을 한번에 종료 가능
  - Label: 반복문 앞에 콜론과 함께 쓰이는 식별자

```js

end: for (...) {
  for(...) {
    break end;
  }
}

/* 이중 for문이 종료된다 */

```

### continue

- 반복문 수행 시 코드 블록 실행을 해당 라인에서 중지하고 
  ( continue 뒤에 있는 코드를 Skip )
  블록 코드를 종료 시킨 후 반복문 내 명시된 조건 판단

