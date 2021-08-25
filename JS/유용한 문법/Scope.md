# Scope 란 무엇일까?

* Scope 란, 우리가 변수 혹은 함수를 선언하게 될 때 해당 변수 또는 함수가 유효한 범위를 의미한다.
  이 스코프에서 3가지가 있다.
```markdown
1. Global (전역) Scope: 코드의 모든 범위에서 사용이 가능합니다.
2. Function (함수) Scope: 함수 안에서만 사용이 가능합니다.
3. Block (블록) Scope: if, for, switch 등 특정 블록 내부에서만 사용이 가능합니다.
```
### 예시를 통해 Scope를 이해해보자

```javascript
const value = 'hello!';

function myFunction() {
  console.log('myFunction: ');
  console.log(value);
}

function otherFunction() {
  console.log('otherFunction: ');
  const value = 'bye!';
  console.log(value);
}

myFunction();
otherFunction();

console.log('global scope: ');
console.log(value);
```

코드의 맨 윗줄에서 선언된 `value` 값은 Global Scope 로 선언된 값이다. Global Scope 로 선언된 값은 어디서든지 사용이 가능하다.

`otherFunction` 에서는 함수 내부에서 `value` 값을 'bye!' 로 새로 선언을 해주었다. 이렇게 되면, `value` 라는 값은 Function Scope 로 지정이 되서 해당 값은 `otherFunction` 내부에서만 유효한 값이 된다. 이렇게 값을 설정한다고 해서 기존에 Global Scope 로 선언된 `value` 값이 바뀌지 않는다.  
<br>
  
또 다른 예시를 봐보도록 하자.

```javascript
const value = 'hello!';

function myFunction() {
  const value = 'bye!';
  const anotherValue = 'world';
  function functionInside() {
    console.log('functionInside: ');
    console.log(value);
    console.log(anotherValue);
  }
  functionInside();
}


myFunction()
console.log('global scope: ');
console.log(value);
console.log(anotherValue);
```

`myFunction` 내부에 `anotherValue` 라는 새로운 값을 선언했고, `functionInside` 라는 함수도 선언을 했다. `functionInside` 함수에서는 `myFunction` 에서 선언한 `value` 값과 `anotherValue` 값을 조회 할 수 있다.

반면, `myFunction` 밖에서는 `anotherValue` 를 조회 할 수 없다.
<br>

다른 예제다.

```javascript
const value = 'hello!';

function myFunction() {
  const value = 'bye!';
  if (true) {
    const value = 'world';
    console.log('block scope: ');
    console.log(value);
  }
  console.log('function scope: ');
  console.log(value);
}

myFunction();
console.log('global scope: ');
console.log(value);
```

`const` 로 선언한 값은 Block Scope 로 선언이 된다. 따라서, if 문 같은 블록 내에서 새로운 변수/상수를 선언하게 된다면, 해당 블록 내부에서만 사용이 가능하며, 블록 밖의 범위에서 똑같은 이름을 가진 값이 있다고 해도 영향을 주지 않는다.

let 또한 마찬가지이다.

하지만 var는 Function Scope 로 선언이 되므로, if 문 블록 내부에서 선언한 value 값이 블록 밖의 value 에도 영향을 미치게 된다.

```javascript
var value = 'hello!';

function myFunction() {
  var value = 'bye!';
  if (true) {
    var value = 'world';
    console.log('block scope: ');
    console.log(value);
  }
  console.log('function scope: ');
  console.log(value);
}

myFunction();
console.log('global scope: ');
console.log(value);
```