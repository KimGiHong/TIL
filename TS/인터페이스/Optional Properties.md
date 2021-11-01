# 선택적 프로퍼티 ( Optional Properties )

인터페이스의 모든 프로퍼티가 필요한 것은 아니다. 어떤 조건에서만 존재하거나 아예 없을 수도 있다. 선택적 프로퍼티들은 객체 안의 몇 개의 프로퍼티만 채워 함수에 전달하는 "option bags" 같은 패턴을 만들 때 유용하다.

`Option Bags 패턴`의 예제
```ts
interface SquareConfig{
    color?: string;
    width?: number;
}

function createSquare(config: SquareConfig): {color: string; area: number;}{
    let newSquare = {color: "white", area: 100};
    if (config.color){
        // Error: Property 'clor' does not exist on type 'SquareConfig'
        // newSquare.color = config.clor;
        newSquare.color = config.color;
    }
    if (config.width){
        newSquare.area = config.width * config.width;
    }
    return newSquare;
}
let mySquare = createSquare({color: "black"});
```

선택적 프로퍼티를 가지는 인터페이스는 다른 인터페이스와 비슷하게 작성되고, 선택적 프로퍼티는 선언에서 프로퍼티 이름 끝에 `?`를 붙여 표시한다.

선택적 프로퍼티의 이점은 인터페이스에 속하지 않는 프로퍼티의 사용을 방지하면서, 사용 가능한 속성을 기술하는 것.
위 주석과 같이 `createColor`안의 `color` 프로퍼티 이름을 잘못 입력하면, 오류 메세지로 알려준다.