# 첫 번째 인터페이스

어떻게 인터페이스가 동작하는지 확인하는 가장 쉬운 방법은 간단한 예제로 시작하는 것이었다.

```Ts
function printLabel(lableledObj: { label: string}){
    consoloe.log(labeledObj.label);
}

let myObj = {size: 10, label: "Size 10 Object};
printLabel(myObj);
```

타입 검사는 `printLabel` 호출을 확인한다. `printLabel`함수는 `string`타입 `label`을 갖는 객체를 하나의 매개변수로 갖는다. 이 객체가 실제로는 더 많은 프로퍼티를 갖고 있지만, 컴파일러는 **최소로** 필요한 프로퍼티가 있는지와 타입이 잘 맞는지만 검사한다.

문자열 타입의 프로퍼티 `label`을 가진 인터페이스로 위 예제를 다시 작성해 보았다.

```Ts
interface LabeledValue {
    label: string;
}

function printLabel(labeledObj: LabeledValue) {
    console.log(labeledObj.label);
}

let myObj = {size: 10, label: "Size 10 Object"};
printLabel(myObj);
```

`LabeledValue` 인터페이스는 이전 예제의 요구사항을 똑같이 기술하는 이름으로 사용할 수 있다. 이 인터페이스는 여전히 **문자열**타입의 label 프로퍼티 하나를 가지는 것을 의미한다. 다른 언어처럼 `printLabel`에 전달한 객체가 이 인터페이스를 구현해야 한다고 명시적으로 애기할 필요는 없다. 여기서 중요한 것은 `형태`뿐이다. 함수에 전달된 객체가 나열된 요구 조건을 충족하면, 허용된다.