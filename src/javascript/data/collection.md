# Collection

- 구조 혹은 비구조화 형태로 프로그래밍 언어가 제공하는 값을 담을 수 있는 공간
- 자바스크립트에서 제공하는 Collection
  - indexed collection
    - array
    - typed array
  - keyed collection
    - Object
    - Map
    - Set
    - Weak Map
    - Weak Set

## Map
- 다양한 자료형의 Key를 허용하고, key-value 형태의 자료형을 저장할 수 있는 Collection
- Object와 비교하면 다양한 key의 사용을 허용하고, 값의 추가/삭제 시 메서드를 통해 수행이 필요하다
- 대표 속성 및 메서드
  - size
  - set
  - get
  - delete
  - clear
  - has
  - keys
  - values
  - entires
  - ...

```js

let mapList = new Map([
  [key, val],
  [key, val],
  [key, val],
]);

for (let item of mapList.values())
for (let item of mapList.keys())
for (let entity of mapList)

let toObj = Object.fromEntries(mapList);
/* 객체형태로 전환됨 */

let toObj = Object.entries(mapList);
/* 리스트 형태로 전환됨 */

```

## Set
- value만을 저장하며 중복을 허용하지 않는 Collection
- 다양한 자료형을 value로 사용 가능하며, add 호출 시 set이 반환되므로 체이닝(chaining)이 가능하다
- 중복된 데이터를 제거할 때 많이 사용됨
- 대표 속성 및 메서드
  - size
  - add
  - delete
  - clear
  - has
  - keys
  - values
  - entries
  - ...

- for문을 사용하게 될 경우 value만을 반환한다
  - Map과의 호환성을 위해 entries의 경우 key와 value가 같은 값으로 쌍을 이룬 리스트가 반환된다.