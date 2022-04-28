# 자바스크립트란?

- 객체(Object) 기반의 스크립트 프로그래밍 언어
  - 인터프리터 형식의 언어 (vs 컴파일 언어)
- ECMAScript 사양을 준수하는 범용 프로그래밍 언어
- 웹의 동적 동작을 구현하기 위해 제작된 언어
- Mocha -> LiveScript -> Javascript로 명칭이 변경됨
- JS 엔진위에서 수행되며, Google V8, Firefox SpiderMonkey, Edge Chakra 가 존재한다.

## ECMAScript란?

- Ecma International ECMA-262 기술 규격에 따라 정의하고 있는 표준화된 스크립트 프로그래밍 언어
- 자바스크립트를 표준화하기 위해 만들어졌으며, 액션스크립트와 J스크립트 등 다른 구현체도 포함
- Ecma International: 정보 통신에 대한 표준을 제정하는 비영리 표준화 기구
- ECMA-262: Ecma International에서 제정한 기술 규격의 이름으로, 범용 목적의 스크립트 언어 명세 기술
- 97년 ES1 초판, 09년 ES5, 15년 ES2015(ES6)으로 매해 6월에 버전을 갱신중이다.
  - 15년부터 년도가 뒤에 붙는 방식으로 이름이 바뀜

## 자바스크립트 변환 절차

1. 소스코드를 Parsing
2. Abstract Syntax Tree
3. lgnition Bytecode (complied code)
