# Promise

프로미스는 비동기 작업을 조금 더 편하게 처리 할 수 있도록 ES6 에 도입된 기능이다. 
이전에는 비동기 작업을 처리 할 때에는 콜백 함수로 처리를 해야 했었는데,
콜백 함수로 처리를 하게 된다면 비동기 작업이 많아질 경우 코드가 쉽게 난잡해지게 되었다고 한다.

숫자 n 을 파라미터로 받아와서 다섯번에 걸쳐 1초마다 1씩 더해서 출력하는 작업을 setTimeout 으로 구현해보도록 하겠다.

```javascript
function increaseAndPrint(n, callback) {
  setTimeout(() => {
    const increased = n + 1;
    console.log(increased);
    if (callback) {
      callback(increased);
    }
  }, 1000);
}

increaseAndPrint(0, n => {
  increaseAndPrint(n, n => {
    increaseAndPrint(n, n => {
      increaseAndPrint(n, n => {
        increaseAndPrint(n, n => {
          console.log('끝');
        });
      });
    });
  });
});
```

코드 읽기가 많이 많이 매우 복잡하다. 이런 식의 코드를 콜백지옥이라고 불린다.

비동기적으로 처리해야 하는 일이 많아질수록, 코드의 깊이가 계속 깊어지는 현상이 있는데, 
Promise 를 사용하면 이렇게 코드의 깊이가 깊어지는 현상을 방지 할 수 있다.


# Promise를 만들어보자

```javascript
const myPromise = new Promise((resolve, reject) => {
  // 구현..
})
```

Promise 는 성공 할 수도 있고, 실패 할 수도 있다. 성공 할 때에는 resolve 를 호출해주면 되고, 실패할 때에는 reject 를 호출해주면 된다. 여기서는 1초 뒤에 성공시키는 상황에 대해서만 구현을 해보도록하자.

```javascript
const myPromise = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve(1);
  }, 1000);
});

myPromise.then(n => {
  console.log(n);
});
```

resolve 를 호출 할 때 특정 값을 파라미터로 넣어주면, 이 값을 작업이 끝나고 나서 사용 할 수 있다. 
작업이 끝나고 나서 또 다른 작업을 해야 할 때에는 Promise 뒤에 `.then(...)` 을 붙여서 사용하면 된다.

이번에는, 1초뒤에 실패되게끔 해보자.

```javascript
const myPromise = new Promise((resolve, reject) => {
  setTimeout(() => {
    reject(new Error());
  }, 1000);
});

myPromise
  .then(n => {
    console.log(n);
  })
  .catch(error => {
    console.log(error);
  });
```

실패하는 상황에서는 `reject` 를 사용하고, `.catch` 를 통하여 실패했을시 수행 할 작업을 설정 할 수 있다.

이제, Promise 를 만드는 함수를 작성해보자.

```javascript
function increaseAndPrint(n) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const value = n + 1;
      if (value === 5) {
        const error = new Error();
        error.name = 'ValueIsFiveError';
        reject(error);
        return;
      }
      console.log(value);
      resolve(value);
    }, 1000);
  });
}

increaseAndPrint(0).then((n) => {
  console.log('result: ', n);
})
```

여기까지만 보면, 그냥 함수를 전달하는건데, 뭐가 다르지 싶을수도 있을 것이다. 하지만, Promise 의 속성 중에는, 만약 then 내부에 넣은 함수에서 또 Promise 를 리턴하게 된다면, 연달아서 사용 할 수 있다.

Like This

```javascript
function increaseAndPrint(n) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const value = n + 1;
      if (value === 5) {
        const error = new Error();
        error.name = 'ValueIsFiveError';
        reject(error);
        return;
      }
      console.log(value);
      resolve(value);
    }, 1000);
  });
}

increaseAndPrint(0)
  .then(increaseAndPrint)
  .then(increaseAndPrint)
  .then(increaseAndPrint)
  .then(increaseAndPrint)
  .then(increaseAndPrint)
  .catch(e => {
    console.error(e);
  });
```

Promise 를 사용하면, 비동기 작업의 개수가 많아져도 코드의 깊이가 깊어지지 않게 된다.

하지만, 이것도 불편한점이 있긴 하다. 에러를 잡을 때 몇번째에서 발생했는지 알아내기도 어렵고 특정 조건에 따라 분기를 나누는 작업도 어렵고, 특정 값을 공유해가면서 작업을 처리하기도 까다롭다. 그래서 async/await 을 사용한다, async/await를 사용한다면 이러한 문제점을 깔끔하게 해결 가능하다.