# slice

* slice 는 splice 랑 조금 비슷하고, 배열을 잘라낼 때 사용하는데, 중요한 점은 기존의 배열은 건들이지 않는 다는 것이다.

```javascript
const numbers = [10, 20, 30, 40];
const sliced = numbers.slice(0, 2); // 0부터 시작해서 2전까지

console.log(sliced); // [10, 20]
console.log(numbers); // [10, 20, 30, 40]
```

slice 에는 두개의 파라미터를 넣게 되는데 첫번째 파라미터는 어디서부터 자를지, 그리고 두번째 파라미터는 어디까지 자를지 를 의미한다.