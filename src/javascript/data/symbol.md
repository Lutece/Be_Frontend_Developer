# 심볼

**Symbol**
- 심볼은 ES2015에서 도입된 원시타입입니다.
- 데이터의 유일함을 나타낼 때 사용됩니다.
- 심볼은 다른 원시타입과는 달리 Symbol() 함수를 호출해 생성한다.
  - 심볼은 원시타입이기 때문에 new 키워드를 사용하지 않는다.
- 심볼은 비공개 객체 멤버를 만들기 위한 한 가지 방법으로 출발했다.
- 심볼 참조 없이 접근할 수 없는 열거 불가능 프로퍼티를 만드는데 사용된다.
- 외부 개발자로부터 보호할 필요가 있는 기능에 적합하다
- 접근을 제한하는 방식을 제공한다.
    - 기존의 방식은 프로퍼티의 문자열에 의존한다.
    - 심볼로 멤버를 만들면 멤버를 만든 심볼로만 그 멤버를 접근할 수 있다.
- 기존 객체 동작 알고리즘을 확장할 수 있다.
  - Symbol.iterator()메서드를 사용해 기존 객체가 iterator 객체로 재정의할 수 있다.
    

심볼은 리터럴 형태가 없다.

```jsx
let firstName = Symbol("first name"); // 심볼 내 문자열은 심볼을 구분짓는 역할을 한다.
let person = {};
person[firstName] = "Nicholas"
console.log(person[firstName]); // "Nicholas"
console.log(firstName); // "Symbol(first name)"
```

- 심볼 인자에 문자열은 toString() 호출 시 [[Description]] 프로퍼티에 저장된다.
- 원시 값을 구분하기 위해 typeof 연산자를 사용한 결과는 ‘symbol’ 값을 반환한다.
- Object.getOwnPropertySymbols();
  - 객체가 갖고있는 심볼들을 반환하는 메서드

## 전역 심볼

- Symbol은 유일한 값과 전역 값을 나눠 사용할 수 있다.
- Symbol.for은 전역 심볼 저장소를 검색 후 값이 있으면 반환한다.
- Symbol.keyFor(Symbol 값) 메서드는 전역 심볼 저장소의 키를 반환
  - 인자로 들어간 심볼 값이 전역 값인지 아닌 지 구분할 수 있다.
- 전역 심볼은 중복을 피하기 위해 prefix를 사용하는 것이 좋다.

```jsx

Symbol('uid') === Symbol('uid') //false
Symbol.for('uid') === Symbol.for('uid') //true

```

## 상용 심볼 (Well-known Symbols)

- 미리 정의되어있는 심볼들
- 자바스크립트의 API 명세를 개발자들에게 드러내기 위한 수단으로 사용되는 심볼
    - ECMAScript 6

```jsx
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
