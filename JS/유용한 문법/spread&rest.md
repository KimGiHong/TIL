# spread 와 rest 문법
>ES6부터 도입된 문법이다.

## spread

spread는 영어이다. 한국말로 펼치다,퍼뜨리다 라는 의미가 있다.
뜻과 비슷하게 spread는 객체 또는 배열을 펼칠 수 있다

```javascript
const slime = {
  name: '슬라임'
};

const cuteSlime = {
  ...slime,
  attribute: 'cute'
};

const purpleCuteSlime = {
  ...cuteSlime,
  color: 'purple'
};

console.log(slime);
console.log(cuteSlime);
console.log(purpleCuteSlime);
```

여기서 사용한 `...`문자가 바로 spread 연산자이다.
원래는 중복하여 작성할 코드들을 spread 문법을 사용하여 더 간단하게 작성가능하다.

spread 연산자는 배열에서 또한 사용 가능하다.

```javascript
const animals = ['개', '고양이', '참새'];
const anotherAnimals = [...animals, '비둘기'];
console.log(animals);
console.log(anotherAnimals);
```

기존의 animals 는 건드리지 않으면서, 새로운 anotherAnimals 배열에 animals 가 가지고 있는 내용을 모두 집어넣고, '비둘기' 라는 항목을 추가적으로 넣었다.

배열에서 spread 연산자를 여러번 사용 할 수도 있다.

```javascript
const numbers = [1, 2, 3, 4, 5];
const spreadNumbers = [...numbers, 1000, ...numbers];
```


## rest

* rest는 spread랑 비슷한데 역할이 다르다.
rest는 객체, 배열, 그리고 함수의 파라미터에서 사용이 가능하다.

### 객체에서의 rest

```javascript
const purpleCuteSlime = {
  name: '슬라임',
  attribute: 'cute',
  color: 'purple'
};

const { color, ...rest } = purpleCuteSlime;
console.log(color);
console.log(rest);
```

rest 안에 name 을 제외한 값들이 들어가 있다.

rest 는 객체와 배열에서 사용할 때 비구조화 할당과 함께 사용된다. 주로 사용할 때는 `rest` 키워드를 사용하긴 하는데 굳이  추출할 값의 이름을 `rest` 로 사용할 필요는 없다.

attribute 까지 없앤 새로운 객체를 만들고 싶다면 이렇게 해주면 될 것 같다.

```javascript
const purpleCuteSlime = {
  name: '슬라임',
  attribute: 'cute',
  color: 'purple'
};

const { color, ...cuteSlime } = purpleCuteSlime;
console.log(color);
console.log(cuteSlime);

const { attribute, ...slime } = cuteSlime;
console.log(attribute);
console.log(slime);
```


### 배열에서의 rest

EX ) 
```javascript
const numbers = [0, 1, 2, 3, 4, 5, 6];

const [one, ...rest] = numbers;

console.log(one);
console.log(rest);
```
배열 비구조화 할당을 통하여 원하는 값을 밖으로 꺼내고, 나머지 값을 rest 안에 넣었다.

근데 이렇게는 못한다고 한다.

```javascript
const numbers = [0, 1, 2, 3, 4, 5, 6];

const [..rest, last] = numbers;
```


### 함수 파라미터에서의 rest

예를 들어서 파라미터로 넣어준 모든 값들을 합해주는 함수를 만들어주고 싶다고 가정해보자.

```javascript
function sum(a, b, c, d, e, f, g) {
  let sum = 0;
  if (a) sum += a;
  if (b) sum += b;
  if (c) sum += c;
  if (d) sum += d;
  if (e) sum += e;
  if (f) sum += f;
  if (g) sum += g;
  return sum;
}

const result = sum(1, 2, 3, 4, 5, 6);
console.log(result);
```

이렇게 함수의 파라미터가 몇개가 될 지 모르는 말도안되는 상황에서 rest 파라미터를 사용하면 매우 유용하다.

```javascript
function sum(...rest) {
  return rest;
}

const result = sum(1, 2, 3, 4, 5, 6);
console.log(result);
```

파라미터들이 들어가있는 배열을 받았으니 이제 모두 더하면 되겠다.

```javascript
function sum(...rest) {
  return rest.reduce((acc, current) => acc + current, 0);
}

const result = sum(1, 2, 3, 4, 5, 6);
console.log(result); // 21
```


### 함수 인자와 spread

* 함수에서 값을 읽을때, 그 값들은 파라미터라고 부른다.
그리고 함수에서 값을 넣어줄 때, 그 값들은 인자라고 부른다.

함수파라미터와 rest 를 사용한 것과 비슷한데, 반대의 역할이다. 예를 들어, 우리가 배열 안에 있는 원소들을 모두 파라미터로 넣어주고 싶다고 가정을 해보겠다.

```javascript
function sum(...rest) {
  return rest.reduce((acc, current) => acc + current, 0);
}

const numbers = [1, 2, 3, 4, 5, 6];
const result = sum(
  numbers[0],
  numbers[1],
  numbers[2],
  numbers[3],
  numbers[4],
  numbers[5]
);
console.log(result);
```

이 방법을 쓰는 사람은 굉장히 불쌍한 사람일 것이다.

sum함수를 사용 할 때 인자 부분에서 spread 를 사용하면 다음과 같이 표현이 가능하다.

```javascript
function sum(...rest) {
  return rest.reduce((acc, current) => acc + current, 0);
}

const numbers = [1, 2, 3, 4, 5, 6];
const result = sum(...numbers);
console.log(result);
```

코드가 보기 좋게 줄어들었다 매우 편안하다.

이렇게, spread 와 rest 를 잘 사용하면 앞으로 보기 깔끔한 코드를 작성하는 것에 큰 도움을 줄 것이다.


