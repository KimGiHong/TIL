# Any
애플리케이션을 만들 때, 알지 못하는 타입을 표현해야 할 수도 있다. 이 값들은 사용자로부터 받은 데이터나 서드 파티 라이브러리 같은 동적인 컨텐츠에서 올 수도 있다. 이 경우 타입 검사를 하지 않고, 그 값들이 컴파일 시간에 검사를 통과하길 원한다. 이를 위해 `any`타입을 사용할 수 있다.

> 서드 파티 라이브러리란? 개인 개발자나 프로젝트 팀, 혹은 업체등에서 개발하는 라이브러리, 즉 제 3자 라이브러리.

```Ts
let notSure: any = 4;
notSure = "maybe a string instead";
notSure = false; //성공, 분명히 bool이다.
```

any 타입은 기존에 JS로 작업할 수 있는 강력한 방법으로, 컴파일 중에 점진적으로 타입 검사를 하거나 하지 않을 수 있다. 혹 다른 언어에서 그렇듯, Object가 비슷한 역할을 할 수 있을 것 같다고 생각할 수도 있다. 그런데, Object로 선언된 변수들은 오직 어떤 값이든 그 변수에 할당할 수 있게 해주지만 실제로 메서드가 존재하더라도, 임의로 호출할 수는 없다.

```Ts
let notSure: any = 4;
notSure.ifItExists(); // 성공, ifItExists는 런타임엔 존재할 것이다.
notSure.toFixed(); // 성공, toFixed는 존재한다. 하지만 컴파일러는 검사하지 않는다.

let prettySure: Object = 4;
prettySure.toFixed(); // 오류, 프로퍼티 'toFixed'는 'Object'에 존재하지 않는다.
```

또한, any타입은 타입의 일부만 알고 전체는 알지 못할 때 유용하다. 예를 들어, 여러 타입이 섞인 배열을 다룰 수 있다.

```Ts
let list: any[] = [1, true, "free"];

list[1] = 100;
```