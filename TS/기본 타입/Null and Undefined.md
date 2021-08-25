# Null and Undefined

TypeScript는 `undefined`와 `null`은 둘 다 각각 자신의 타입 이름으로 `undefined`, `null`로 사용한다. `void`처럼 그 자체로 유용한 경우는 거의 없다.

```Ts
// 이 밖에 이 변수들에 할당할 수 있는 값은 없다.
let u: undefined = undefined;
let n: null = null;
```

기본적으로 `null`과 `undefined`는 다른 모든 타입의 하위 타입이다. 이건 null과 undefined를 `number` 같은 타입에 할당할 수 있다는 것을 의미한다.

하지만, `--strictNullChecks`를 사용하면, `null`과 `undefined`는 오직 `any`와 각자 자신들 타입에만 할당 가능하다. ( 에외적으로 `undefined`는 `void`에 할당 가능하다. ) 이건 많은 일반적인 에러를 방지하는 데 도움을 준다. 이 경우, `string` 또는 `null` 또는 `undefined`를 허용하고 싶은 경우 유니언 타입인 `string | null | undefined`를 사용할 수 있다.