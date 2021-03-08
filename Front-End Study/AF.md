# 익명함수(Anonymouse Function)

* 익명함수 또는 무명함수같은 경우는 따로 사용자가 함수를 만들 때 이름을 지정하지 않고 변수 혹은 그냥 호출만으로 선언할 수 있는 함수 입니다. 

> 익명함수 같은 경우는 브라우저가 런타임(RunTime)에 동적으로 선언되는 함수입니다.

```javascript
let func = function (){
  const selector = document.getElementById("func");
  selector.innerHTML = "익명 함수 입니다.";
};

func();
```
위 코드와 같이 이런식으로 사용이 가능합니다. 비록 익명함수 같은경우는 func라는 이름을 가지고 있지만. func는 그저 함수를 가지고 있는 변수에 불과하므로 이름을 가지고 있다고는 말 할 수 없습니다.