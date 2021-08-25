# reduce

`reduce` 함수는 잘 사용 할 줄 알면 정말 유용한 내장 함수이다.`잘 사용 못하니 공부하도록 하자`

예제 ) 만약 주어진 배열에 대하여 총합을 구해야 하는 상황이 왔다고 가정해보도록 하자.

```javascript
const numbers = [1, 2, 3, 4, 5];

let sum = 0;
numbers.forEach(n => {
  sum += n;
});
console.log(sum);
```

`결과는 15가 나온다`

여기서 sum 을 계산하기 위해서 사전에 sum 을 선언하고, forEach 를 통하여 계속해서 덧셈을 해주었다.

여기서 reduce 라는 함수를 사용하면 다음과 같이 구현 할 수 있다.

```javascript
const numbers = [1, 2, 3, 4, 5];
let sum = array.reduce((accumulator, current) => accumulator + current, 0);

console.log(sum);
```

`reduce` 함수에는 두개의 파라미터를 전달한다. 
첫번째 파라미터는 accumulator 와 current 를 파라미터로 가져와서 결과를 반환하는 콜백함수이고, 
두번째 파라미터는 reduce 함수에서 사용 할 초깃값이다.

여기서 accumulator 는 누적된 값을 의미한다.

`reduce`함수를 이용하면

```javascript
const numbers = [1, 2, 3, 4, 5];
let sum = numbers.reduce((accumulator, current) => {
  console.log({ accumulator, current });
  return accumulator + current;
}, 0);

console.log(sum);
```

이 코드의 실행 결과는 
```javscript
> Object {accumulate : 0, current : 1}
> Object {accumulate : 1, current : 2}
> Object {accumulate : 3, current : 3}
> Object {accumulate : 6, current : 4}
> Object {accumulate : 10, current : 5}
15
```

배열을 처음부터 끝까지 반복하면서 우리가 전달한 콜백 함수가 호출이 되었다, 가장 처음엔 accumulator 값이 0 이다. 이 값이 0인 이유는 우리가 두번째 파라미터인 초깃값으로 0을 설정했기 때문이다.

처음 콜백 함수가 호출되면, 0 + 1 을 해서 1이 반환이 된다. 이렇게 1일 반환되면 그 다음 번에 콜백함수가 호출 될 때 accumulator 값으로 사용된다.

콜백함수가 두번째로 호출 될 땐 1 + 2 를 해서 3이되고, 이 값이 세번째로 호출될 때의 accumulator 가 된다.

그래서 계속 누적돼어 15라는 결과물이 나타나게 된다.

reduce 를 사용해서 평균도 계산 할 수 있다. 평균을 계산하려면, 가장 마지막 숫자를 더하고 나서 배열의 length 로 나누어주어야 한다.

```javascript
const numbers = [1, 2, 3, 4, 5];
let sum = numbers.reduce((accumulator, current, index, array) => {
  if (index === array.length - 1) {
    return (accumulator + current) / array.length;
  }
  return accumulator + current;
}, 0);

console.log(sum);
```

위 코드의 reduce 에서 사용한 콜백함수에서는 추가 파라미터로 index 와 array 를 받아왔다. 
index 는 현재 처리하고 있는 항목이 몇번째인지 가르키고, array 는 현재 처리하고 있는 배열 자신을 의미한다.