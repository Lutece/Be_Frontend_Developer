# 심볼

**Symbol**

## 요약
- 심볼은 ES2015에서 도입된 원시타입이다.
- 값의 유일함을 나타낼 때 사용된다.
- 심볼은 다른 원시타입과는 달리 Symbol() 함수를 호출해 생성한다.
  - 심볼은 원시타입이기 때문에 new 키워드를 사용하지 않는다.
- 접근을 제한하는 방식을 제공한다.
    - 기존의 방식은 프로퍼티의 문자열에 의존한다.
    - 심볼로 멤버를 만들면 멤버를 만든 심볼로만 그 멤버를 접근할 수 있다.
- 기존 객체 동작 알고리즘을 확장할 수 있다.
  - Symbol.iterator()메서드를 사용해 기존 객체가 iterator 객체로 재정의될 수 있다.
- 심볼 인자에 문자열은 toString() 호출 시 [[Description]] 프로퍼티에 저장된다.
- 원시 값을 구분하기 위해 typeof 연산자를 사용한 결과는 ‘symbol’ 값을 반환한다.
- Object.getOwnPropertySymbols();
  - 객체가 갖고있는 심볼들을 반환하는 메서드

```jsx

let firstName = Symbol("first name"); // 심볼 내 문자열은 심볼을 구분짓는 역할을 한다.
let person = {};
person[firstName] = "Nicholas"
console.log(person[firstName]); // "Nicholas"
console.log(firstName); // "Symbol(first name)"

```

## 전역 심볼

- Symbol은 유일한 값과 전역 값을 나눠 사용할 수 있다.
- Symbol.for은 전역 심볼 저장소를 검색 후 값이 있으면 반환한다.
  - 값이 없으면 새로운 심볼 값을 전역 심볼 저장소에 생성한 후 생성된 심볼 값을 반환한다.
- Symbol.keyFor(Symbol 값) 메서드는 전역 심볼 저장소의 키를 반환한다.
  - 인자로 들어간 심볼 값이 전역 값인지 아닌 지 구분할 수 있다.
    - 전역 값일 경우 심볼 인자값이 반환된다. 아닐 경우 undefined를 반환한다.
- 전역 심볼은 중복을 피하기 위해 prefix를 사용하는 것이 좋다.

```jsx

Symbol('uid') === Symbol('uid') //false

const test1 = Symbol.for('test1');
const test2 = Symbol.for('test1');

console.log(test1 === test2); //true;

```

## 심볼과 프로퍼티 키
- 심볼 값은 유일무이한 값이므로 심볼 값으로 프로퍼티 키를 만들면 다른 프로퍼티 키와 절대 충돌하지 않는다.
- 심볼 값으로 키를 만들게되면 그 키는 은닉화가 된다.
  - getOwnPropertySymbols 메서드를 통해서만 찾을 수 있다.

```js

const obj  = {
  [Symbol('mySymbol')]: 1
};

for(const key in obj) {
  console.log(key) //아무것도 출력되지 않음
}

```

## 심볼과 표준 빌트인 객체 확장
- 표준 빌트인 객체에 사용자 정의 메서드를 문자열로 직접 추가하여 확장하는 것은 권장하지 않는다.

```js

Array.prototype.sum = function() {
  return this.reduce((acc, cur) => acc + cur, 0);
}

```
- 이렇게 커스텀하게 확장하게 되면 미래의 표준사양과 충돌이 있을 수 있다. 표준사양이 같은 키로 추가되면 표준 사양으로 값이 덮어쓰이게 된다. 이로인해 문제가 발생될 수 있다.
- 이럴 때 심볼을 사용하게 되면 미래의 표준사양이 반영되더라도 영향을 받지 않게 된다.
- 새로 생성한 키 또한 이전에 만들어진 키와 중복되지 않아 하위호환성을 보장한다.

## 상용 심볼 (Well-known Symbols)

- 미리 정의되어있는 심볼들

```js

console.log(Symbol);

```

- 자바스크립트의 API 명세를 개발자들에게 드러내기 위한 수단으로 사용되는 심볼
    - ECMAScript 6
    - 시스템 심볼(System Symbol)이라 부르기도 한다.
    - 자바스크립트 엔진의 내부 알고리즘에 사용된다.
      - ex) iterable
        - iterable은 Symbol.iterator를 키로 갖는 메서드를 가지며, Symbol.iterator 메서드를 호출하면 iterator를 반환하도록 ECMA사양에 규정되어 있다. = iteration protocol

```js

function Car(make, model, year) {
  this.make = make;
  this.model = model;
  this.year = year;
}

const auto = new Car('Honda', 'Accord', 1998);

auto instanceof Car // true
Car[Symbol.hasInstance](auto); //true

Car[Symbol.hasInstance](auto) 의 단축문법 === instanceof

```

## 상용 심볼의 예

Symbol.hasInstance
- 객체의 상속을 확인하기 위해 instanceof에 의해 사용되는 메서드
- 모든 함수는 주어진 객체가 그 함수의 인스턴스인지를 확인하는 Symbol.hasInstance를 가진다.

Symbol.iterator
- 이터레이터를 반환하는 메서드

## 참고자료
- https://meetup.toast.com/posts/312
- https://ko.javascript.info/symbol
- https://exploringjs.com/es6/ch_symbols.html
- https://tc39.es/ecma262/multipage/ecmascript-data-types-and-values.html#sec-well-known-symbols
- 자바스크립트 Deep Dive