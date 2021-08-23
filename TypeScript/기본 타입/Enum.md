# 열거 (Enum)

JavaScript의 표준 자료형 집합과 사용하면 도움이 될만한 데이터 형은 `enum`이다. C#같은 언어처럼, `enum`은 값의 집합에 더 나은 이름을 붙여줄 수 있다.

```Ts
enum Color { Red, Green, Blue }
let c: Color = Color.Green;
```

기본적으로 `enum`은 0부터 시작하여 멤버들의 번호를 매긴다. 멤버 중 하나의 값을 수동으로 설정하여 번호를 바꿀 수 있다. 예를 들어, 위 예제를 0 대신 1부터 시작해 번호를 매기도록 바꿀 수 있다.

```Ts
enum Color { Red = 1, Green, Blue }
let c: Color = Color.Green;
```

또는, 모든 값을 수동으로 설정할 수 있다.

`enum`의 유용한 기능중 하나는 매겨진 값을 사용해 enum 멤버의 이름을 알아낼 수 있다는 것이다. 예를 들어 위의 예제에서 2라는 값이 위의 어떤 Color enum 멤버와 매칭되는지 알 수 없을 때, 이에 일치하는 이름을 알아낼 수 있다.

```Ts
enum Color { Red = 1, Green, Blue }
let colorName: string = Color[2];

consoloe.log(colorName); // 값이 2인 'Green'이 출력된다.
```