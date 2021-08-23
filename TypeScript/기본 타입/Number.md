# 숫자 (Number)

JS처럼, TS의 모든 숫자는 부동 소수 값이다. 부동 소수에는 `number`라는 타입이 붙혀진다. TS는 16진수, 10진수 리터럴에 더불어, ECMAScript 2015에 소개된 2진수, 8진수 리터럴도 지원한다.

```Ts
let decimal: number = 6;
let hex: number = 0xf00d;
let binary: number = 0b1010;
let octal: number = 0o744;
```