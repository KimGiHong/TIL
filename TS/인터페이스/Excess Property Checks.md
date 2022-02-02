# 초과 프로퍼티 검사 ( Excess Property Checks )

인터페이스의 첫 번째 에제에서 Typescript가 `{ label: string; }`을 기대해도 `{ size: number; label: string;} `을 허용해주었다. 또한 선택적 프로퍼티를 배우고, 소위 "option bags"를 기술할 때, 유용하다는 것을 배웠다.

하지만, 그냥 그 둘을 결합하며 ㄴ에러가 발생할 수 있다. 예를 들어, `createSquare`를 사용한 마지막 에제이다.

```ts 
interface SquareConfig{
    color?: string;
    width?: number;
}

function createSquare(config: SquareConfig): { color: string; area: number } {
    let newSquare = {color: "white", area: 100};
    if (config.clor) {
        // Error: Property 'clor' does not exist on type 'SquareConfig'
        newSquare.color = config.clor;
    }
    if (config.width) {
        newSquare.area = config.width * config.width;
    }
    return newSquare;
}

let mySquare = createSquare({ colour: "red", width: 100});
```

`createSquare`의 매개변수가 `color`대신 `colour`로 전달된 것에 유의해야한다. 이 경우 JS에선 조용히 오류가 발생한다.

