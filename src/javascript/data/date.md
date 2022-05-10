# Date
- 표준 Built-in 객체로써 날짜와 시간을 위한 속성값과 메서드를 제공하는 객체
- Date 객체는 1970년 1월 1일 UTC 자정과의 시간 차이를 밀리초로 나타내는 정수 값으로 표현
- 생성자 및 대표 메서드
  - Date(year, month, date, hours, minutes, seconds, ms)
  - ...

## benchmark
- 성능 측정

```js

function benchmark(callback_func) {
  let date_1 = new Date("2020-01-01");
  let date_2 = new Date();

  let start = Date.now();
  for(let i = 0; i < 100000; i++) {
    callback_func(date_1, date_2);
  }

  return Date.now() - start;
}

```