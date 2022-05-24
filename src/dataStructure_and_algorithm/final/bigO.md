# 점근 표기법과 빅오 표기법
## 점근 표기법 (asymptotic notation)
- 정수론과 해석학의 방법
- 어떤 함수가 증가하는 모습을 다른 함수와 비교
- 알고리즘의 복잡도를 논하거나 단순화시킬 때 사용

## 빅오 표기법 (Big-O notation)
- 대문자 O를 이용해 표기
- 주로 알고리즘을 분류하기 위해 사용
  - O(1), O(log n), O(n), O(nlog n), O(n2), O(n!)
- O의 의미
  - order of the function (대략 그 함수 정도)

### 어떤 기준으로 분류하나요?
- **입력 데이터가 많아짐**에 따라 다음 둘이 얼마나 늘어나는지 측정
  - 실행 시간(시간 복잡도)
    - 주로 신경쓰는 부분
    - 입력 데이터가 많아짐에 따라 얼마나 시간이 더 걸리는지
  - 필요한 공간(공간 복잡도)
- 즉, 입력이 증가함에 따른 시간 및 공간의 증가량을 의미
  

### 순서 (실행 속도가 가장 작은 순부터 큰 순서까지)

- O(1) < O(log n) < O(n) < O(nlog n) < O(n2) < O(n!)

### O(1) 알고리즘 (배열 기준)
- 입력 데이터의 크기 N에 상관없이 언제나 일정한 시간이 걸림
- 두 수의 합
  
### O(n) 알고리즘
- 입력 데이터의 크기 N에 비례하는 시간이 걸림
- 예) 모든 수의 총합
  
### O(n 제곱) 알고리즘
- 입력 데이터 크기 N의 제곱에 비례하는 시간이 걸림
  
### O(log n) 알고리즘
- O(1)과 O(n)사이 = O(n)보다는 빠르다
- 점점 평평해진다.
- log => 지수의 반대

## 알고리즘 평가 지표
- 정확성
- 작업량
- 메모리 사용량
- 최적성
- 효율성
  - 시간 복잡도
    - 입력 크기의 값에 대해 단위 연산을 몇 번 수행하는지 계산하여, 알고리즘의 수행시간을 평가하는 방법
- ![알고리즘](https://t1.daumcdn.net/cfile/tistory/99BBBF375CF419260A)
- ![정렬 알고리즘](https://static.packt-cdn.com/products/9781789805789/graphics/assets/e82896f2-626c-45f7-9ce7-54b0be484b54.png)