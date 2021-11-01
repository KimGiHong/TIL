# 읽기전용 프로퍼티 ( Readonly properties )

일부 프로퍼티들은 객체가 처음 생성될 때만 수정 가능해야한다. 프로퍼팀 이름 앞에 `readonly`를 넣어서 이를 저장할 수 있다.
```ts
interface Point {
    readonly x: number;
    readonly y: number;
}
```

객체 리터럴을 할당하여 `Point`를 생성한다. 할당 후에는 `x`,`y`를 수정이 불가하다.

```ts
let p1:Point = { x: 10, y: 20 };
p1.x = 5; // 오류!
```

Typescript에서는 모든 변경 메서드(`Mutating Methods`)가 제거된 `Array<T>`와 동일한 `ReadonlyArray<T>`타입을 제공한다. 그래서 생성 후에 배열을 변경하지 않음을 보장할 수 있다.

```ts
let a: number[] = [1, 2, 3, 4];
let ro: ReadonlyArray<number> = a;
ro[0] = 12; // 오류
ro.push(5); // 오류
ro.length = 100; // 오류
a = ro; // 오류
```

예제 마지막 줄에서 `ReadonlyArray`를 일반 배열에 재할당이 불가능한 것을 알 수 있다. 타입 단언(type assertion)으로 오버라이드하는 것은 가능하다.

```ts
a = ro as number[];
```