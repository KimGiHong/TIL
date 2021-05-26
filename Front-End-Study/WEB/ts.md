# TypeScript란?
* TypeScript는 JS의 static type checker(코드 실행 없이, error를 detect)이다.
* TypeScript는 `Typed Superset of JS`이다. ( JS 코드를 그대로 오류 없이 실행 가능)
* 실무에서 많은 경우의 오류 원인에 해당하는 type(일종의 올마른 틀,규격)을 미리 정의해 둠으로써, 이로 인한 오류 발생 가능성과 디버깅 수고를 줄일 수 있음.

# TypeScript 기본 이론
1. **Explicit Type Annotation**: 변수나 인자의 type을 직접 정의 / 컴파일 통해 js로 변환되면 모두 사라짐.

```typescript
function greet(person: string, data: Date) {
    console.log(`Hello ${person}, today is ${date.toDateString()}!`);
}
greet("Maddison", Date());
// string 유형의 인수는 Date 유형의 매개 변수에 할당할 수 없다.
```

2. **Infer Types**: 자동으로 type을 인식도 가능 / type system이 추론하는 Type이 동일하다면 굳이 annotation으로 하지 않아도 됨.
```typescript
let msg = "hello there!";
//  ^ = let msg: string
```

3. TypeScript는 JS의 typeof로 확인할 수 있는, string,number,boolean등을 동일하게 포함하며, 특별한 type인 any를 더 포함한다.(type을 규정하지 않고, type system도 추론할 수 없을 때는 default로 any를 할당)

4. **Union Type** : 여러 타입의 종류 중 하나로 표현할 경우 사용