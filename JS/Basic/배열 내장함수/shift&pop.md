# shift 와 pop

* `shift` 와 `pop` 은 비슷하지만, 다르다.
`shift` 는 첫번째 원소를 배열에서 추출해줍니다. (추출하는 과정에서 배열에서 해당 원소는 사라짐)

shift 예제
```javascript
const numbers = [10, 20, 30, 40];
const value = numbers.shift();
console.log(value);
console.log(numbers);
```

위 예제의 결과

`10
[20, 30, 40]`

pop 예제

```javascript
const numbers = [10, 20, 30, 40];
const value = numbers.pop();
console.log(value);
console.log(numbers);
```

위 예제의 결과

`40
[10, 20, 30]`

`pop` 은 `push` 의 반대로 생각하면 될 것 같다. `push` 는 배열의 맨 마지막에 새 항목을 추가하고, `pop` 은 맨 마지막 항목을 추출합니다.