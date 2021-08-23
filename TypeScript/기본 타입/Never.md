# Never

`never`타입은 절대 발생할 수 없는 타입을 나타낸다. 예를 들어 `never`은 함수 표현식이나 화살표 함수 표현식에서 항상 오류를 발생시키거나 절대 반환하지 않는 반환 타입으로 쓰인다. 변수 또한 `타입 가드`에 의해 아무 타입도 얻지 못하게 좁혀지면 `never`타입을 얻게 될 수 있다.

`never`타입은 모든 타입에 할당 가능한 하위 타입이다. 하지만 어떤 타입도 `never`에 할당할 수 있거나, 하위 타입이 아니다. ( `never` 자신은 제외 ) 심지어 `any`도  `never`에 할당할 수 없다.

```Ts
// never를 변환하는 함수는 함수의 마지막에 도달할 수 없다.
function error(message: string): never {
    throw new Error(message);
}

// 반환 타입이 never로 추론된다.
function fail() {
    return error("Something failed");
}

// never를 반환하는 함수는 함수의 마지막에 도달할 수 없다.
function infiniteLoop(): never {
    while(true){
    }
}
```