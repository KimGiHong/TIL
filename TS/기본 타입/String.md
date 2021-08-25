# 문자열 (String)

웹 페이지, 서버 같은 프로그램을 JS로 만들 때 기본적으로 텍스트 데이터를 다루는 작업이 필요하다. 다른 언어들처럼, Ts에서는 텍스트 데이터 타입을 `string`으로 표현한다. JS처럼 TS또한 큰따옴표 ( " )나 작은 따옴표 ( ' )를 문자열 데이터를 감싸는데 사용한다.

```Ts
let color: string = "blue"
color = 'red';
```

또한 *템플릿 문자열*을 사용하면 여러 줄에 걸쳐 문자열을 작성할 수 있으며, 표현식을 포함시킬 수도 있다. 이 문자열은 백틱( ` )문자로 감싸지며, ``` ${ expr } ```과 같은 형태로 표현식을 포함시킬 수 있다.

```Ts
let fullName: string = `Bob Bobbington`;
let age: number = 37;
let sentence: string = `Hello, my name is ${fullName}. I'll be ${ age + 1 } years old next month.`;
```

위는 아래 `sentence`선언과 동일하다.

```Ts
let sentence: string = "Hello, my name is" + fullName + ".\n\n" + "I'll be" + (age+1) + " years old next month.";
```