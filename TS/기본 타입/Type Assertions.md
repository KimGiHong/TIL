# 타입 단언 ( Type assertions )

`타입 단언`은 컴파일러에게 `"날 믿어, 난 내가 뭘 하고 있는지 알아"`라고 말해주는 방법이다. 타입 단언은 다른 언어의 `타입 변환(형 변환)`과 유사하지만, 다른 특별한 검사를 하거나 데이터를 재구성하지는 않는다. 이는 런타임에 영향을 미치지 않으며, 온전히 컴파일러만 이를 사용한다. 타입스크립트는 개발자가 필요한 어떤 특정 검사를 수행했다고 인지한다.

타입 단언에는 두 가지 형태가 있다.  

첫째, `angle-bracket` 문법.

```Ts
let someValue: any = "this is a string";

let strLength: number = (<string>someValue).length;
```

둘째, `as-` 문법.

```Ts
let someValue: any = "this is a string";

let strLength: number = (someValue as string).length;
```

TypeScript와 JSX를 함께 사용할 때는, `as-`스타일의 단언만 허용된다.