# map

* `map` 은 배열 안의 각 원소를 변환 할 때 사용 되며, 이 과정에서 새로운 배열이 만들어진다.

이러한 배열이 있다고 가정해보자,

`const array = [1, 2, 3, 4, 5, 6, 7, 8];`

만약에 배열 안의 모든 숫자를 제곱해서 새로운 배열을 만들고 싶다면 
map 함수를 사용하지 않고 우리가 지금까지 배운 지식들을 활용하면 다음과 같이 구현 할 수 있다.

```javascript
const array = [1, 2, 3, 4, 5, 6, 7, 8];

const squared = [];
for (let i = 0; i < array.length; i++) {
  squared.push(array[i] * array[i]);
}

console.log(squared);
```

또는 위에서 공부한 forEach 를 쓰면 다음과 같이 구현 가능하다.

```javascript
const array = [1, 2, 3, 4, 5, 6, 7, 8];

const squared = [];

array.forEach(n => {
  squared.push(n * n);
});

console.log(squared);
```

하지만 map을 사용하면 조금 더 짧은 코드를 작성 가능하다.
```javascript
const array = [1, 2, 3, 4, 5, 6, 7, 8];

const square = n => n * n;
const squared = array.map(square);
console.log(squared);
```

map 함수의 파라미터로는 변화를 주는 함수를 전달해줍니다. 이를 변화함수라고 부르겠다.

현재 우리의 변화함수 square 는 파라미터 n 을 받아와서 이를 제곱해줍니다.

array.map 함수를 사용 할 때 square 를 변화함수로 사용함으로서, 내부의 모든 값에 대하여 제곱을 해서 새로운 배열을 생성하였다.

변화 함수를 꼭 이름을 붙여서 선언 할 필요는 없다.