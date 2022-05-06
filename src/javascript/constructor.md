# 생성자

- 유사한 객체를 다중으로 만들 때 사용되는 함수 (class 개념과 유사)
- 일반적으로 생성자 함수의 첫 글자는 대문자로 시작
- 생성자 함수로 객체 생성 시 new 연산자를 통해 객체 생성

## new.target

- new.target 속성(property)를 사용하여 new와 함께 호출했는지 확인 가능
- 좀 더 완벽한 생성자 함수를 만들 때 사용하면 좋다.