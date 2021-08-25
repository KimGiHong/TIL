# Hoisting은 뭘까? Hoisting 이해하기

* Hoisting 이란, 자바스크립트에서 아직 선언되지 않은 함수/변수를 "끌어올려서" 사용 할 수 있는 자바스크립트의 작동 방식을 의미한다.

에제로 봐보도록 하자.

```javascript
myFunction();

function myFunction() {
  console.log('hello world!');
}
```

위 코드에서는 `myFunction` 함수를 선언하기 전에, `myFunction()` 을 호출해주었다. 함수가 아직 선언되지 않았음에도 불구하고 코드는 정상적으로 작동하게 된다.

이게 잘 작동하는 이유는, 자바스크립트 엔진이 위 코드를 해석하는 과정에서, 다음과 같이 받아들이게 되기 때문이다.

```javascript
function myFunction() {
  console.log('hello world!');
}

myFunction();
```

이러한 현상을, Hoisting 이라고 부르는 것 같다.
변수 또한 Hoisting 이 된다고 한다.

하지만, `const` 와 `let` 은 Hoisting이 발생하지 않고, 에러가 발생하게 된다.

Hoisting 은 자바스크립트 엔진이 갖고 있는 성질이며, Hoisting 을 일부러 할 필요는 없지만, 방지하는 것이 좋다고 한다. 왜냐하면 Hoisting 이 발생하는 코드는 이해하기 어렵기 때문에 유지보수도 힘들어지고 의도치 않는 결과물이 나타나기 쉽기 때문이다.

Hoisting 을 방지하기 위해서, 함수의 경우 꼭 선언 후에 호출을 하도록 주의를 하도록 하고, var 대신 const, let 을 위주로 사용하자. 추가적으로, 나중에 자바스크립트 개발을 본격적으로 하게 될 때에는 ESLint 라는것을 사용하여 Hoisting 이 발생하는 코드는 에디터상에서 쉽게 발견해낼 수 있을 것이다.