# Void
`void`는 어떤 타입도 존재할 수 없음을 나타내기 떄문에, `any`의 반대 타입과 같다. `void`는 보통 함수에서 반환 값이 없을 때 반환 타입을 표현하기 위해 쓰인다.

```ts
function warnUser(): void {
    console.log("This is my warning message");
}
```

`void`를 타입 변수로 선언하는 것은 유용하지 않는데, 왜냐하면 그 변수에는 `null (--strictNullChecks`을 사용하지 않을 때만 해당) 또는 `undefined`만 할당할 수 있기 때문이다.

```ts
let unusable: void = undefined;
unusable = null; // if don't us '--strictNullChecks'
```