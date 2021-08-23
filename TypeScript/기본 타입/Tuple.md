# 튜플 (Tuple)

튜플 타입을 사용하면, 요소의 타입과 개수가 고정된 배열을 표현할 수 있다. 단 요소들의 타입이 모두 같을 필요는 없다. 예를 들어, `number`, `string`이 쌍으로 있는 값을 나타내고 싶을 수 있다.

```Ts
// 튜플 타입으로 선언
let x: [string, number];

// 초기화
x = ["hello", 10];

// 잘못된 초기화
x = [10, "hello"]
```

정해진 인덱스에 위치한 요소에 접근하면 해당 타입이 나타난다.

```Ts
console.log(x[0].substring(1)); // 성공
console.log(x[1].substring(1)); // 오류, 'number'에는 'substring'이 없다.
```

정해진 인덱스 외에 다른 인덱스에 있는 요소에 접근하면, 오류가 발생하며 실패한다.

```Ts
x[3] = "world"; // 오류, '[string, number]' 타입에는 프로퍼티 '3'이 없다.

console.log(x[5].toString()); // '[string, number]' 타입에는 프로퍼티 '5'가 없다.
```