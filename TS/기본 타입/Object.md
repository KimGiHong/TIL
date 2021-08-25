# 객체
`object`는 원시 타입이 아닌 타입을 나타낸다. 예를 들어 `number`, `string`, `boolean`, `bigint`, `symbol`, `null`, 또는 `undefined`가 아닌 나머지를 의미한다.

`object`타입을 쓰면, `Object.create`같은 API가 더 잘 나타난다.

```Ts
declare function create(O: object | null): void;

create({ prop: 0}); // Success
cretae(null) // Success

create(42); // fail
create("string") //fail
create(false) // fail
create(undefined); // fail
```