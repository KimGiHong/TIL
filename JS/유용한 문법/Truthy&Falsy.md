# Truthy and Falsy

* 그냥 알아두면 좋은 개념

Falsy 한 값들

```javascript
console.log(!undefined);
console.log(!null);
console.log(!0);
console.log(!'');
console.log(!NaN);
```

값들은 모두 true이다.

이 코드 이외의 값든은 모두 Truthy한 값들이라 생각하면 될 것 같다.

Truthy 한 값과 Falsy 한 값은 if 문에서도 사용 할 수있다.

```javascript
const value = { a: 1 };
if (value) {
  console.log('value 가 Truthy 하네요.');
}
```

value 가 Truthy 한 값이기 때문에, 콘솔에 메시지가 출력 될 것이다. 반면, value 가 null, undefined, 0, '', NaN 중 하나라면, 나타나지 않을 것이다.

알아두면 조건문을 작성할 때 편할 것 같다.

추가적으로, 특정 값이 Truthy 한 값이라면 true, 그렇지 않다면 false 로 값을 표현하는 것을 구현하겠다.

```javascript
const value = { a: 1 };

const truthy = value ? true : false;
```

위 코드와 같이 삼항연산자를 이용하면 쉽게 value 값의 존재 유무에 따라 쉽게 true 및 false 로 전환이 가능하다.

근데 이걸 더 쉽게 할 수 있다.

```javascript
const value = { a: 1 };
const truthy = !!value;
```