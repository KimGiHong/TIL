# unshift

* `unshift`는 `shift`의 반대 이다.

위의 예제에서 맨 앞에 새 원소를 추가하면
```javascript
const numbers = [10, 20, 30, 40];
numbers.unshift(5);
console.log(numbers);
```
다음과 같은 결과가 나온다.
`[5, 10, 20, 30, 40]`