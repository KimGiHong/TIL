# 타입 가드

* 특징  
    - 함수 이름에 `isDeveloper`처럼 `is`를 많이 붙인다.
    - `is`는 타입 가드에서 사용되는 키워드이다.

```Ts
// 타입 가드 정의
function isDeveloper(target: Developer | Person):target is Developer {
    return (target as Developer).skill !== undefined;
}
```

* `isDeveloper`함수는 실제 많이 사용하는 패턴이다.
* `target is Developer`은 **넘겨받은 파라미터가 실제 해당 타입인지 구분하는 키워드**라고 해성한다.
* `return (target as Developer).skill !== undefined`는 **target이라는 obj에 skill이 있을 때 Developer 타입이디 라고 취급하겠다는 것**

> 결론적으로 `isDeveloper` 함수의 내부로직을 통과하고 나면  
인자로 넘겼던 값이 `Developer`인지 아닌지 구분해준다.
