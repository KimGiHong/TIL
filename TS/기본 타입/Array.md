# 배열 (Array)
TypeScript는 JavaScript처럼 값들을 배열로 다룰 수 있게 해준다. 배열 타입은 두 가지 방법으로 쓸 수 있다. 첫번째 방법은, 배열 요소들을 나타내는 타입 뒤에 [] 를 쓰는 것이다.

```Ts
let list: number[] = [1, 2, 3];
```

두번째 방법은 제네릭 배열 타입을 쓰는 것이다. `Array<elemType>`:
```Ts
let list: Array<number> = [1, 2, 3];
```