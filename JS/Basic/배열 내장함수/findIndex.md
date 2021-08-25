# findIndex

* 배열 안에 있는 값이 객체이거나, 배열이라면 indexOf 로 찾을 수 없다.

다음과 같은 배열이 있다고 하자.

```javascript
const todos = [
  {
    id: 1,
    text: '자바스크립트 입문',
    done: true
  },
  {
    id: 2,
    text: '함수 배우기',
    done: true
  },
  {
    id: 3,
    text: '객체와 배열 배우기',
    done: true
  },
  {
    id: 4,
    text: '배열 내장함수 배우기',
    done: false
  }
];
```

여기서 만약 id 가 3 인 객체가 몇번째인지 찾으려면, findIndex 함수에 검사하고자 하는 조건을 반환하는 함수를 넣어서 찾을 수 있다.

```javascript
const todos = [
  {
    id: 1,
    text: '자바스크립트 입문',
    done: true
  },
  {
    id: 2,
    text: '함수 배우기',
    done: true
  },
  {
    id: 3,
    text: '객체와 배열 배우기',
    done: true
  },
  {
    id: 4,
    text: '배열 내장함수 배우기',
    done: false
  }
];

const index = todos.findIndex(todo => todo.id === 3);
console.log(index);
```

결과 값은 2가 나오게 된다.