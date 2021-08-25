# find

* `find` 함수는 `findIndex` 랑 비슷한데, 찾아낸 값이 몇번째인지 알아내는 것이 아니라, 찾아낸 값 자체를 반환한다.

위의 예제와 연결하였을 때,
```javascript
const todo = todos.find(todo => todo.id === 3);
console.log(todo);
```

결과는 이렇게 나오게 된다.

`{id: 3, text: "객체와 배열 배우기", done: true}`