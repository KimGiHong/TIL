# forEach

`forEach` 는 가장 쉬운 배열 내장함수이다. 기존에 우리가 배웠던 for 문을 대체 시킬 수 있다

만약, 배열 안에 있는 모든 원소들을 모두 출력해야 한다면 for 문을 사용하여 다음과 같이 구현 할 수 있다,
```javascript
const superheroes = ['아이언맨', '캡틴 아메리카', '토르', '닥터 스트레인지'];

for (let i = 0; i < superheroes.length; i++) {
  console.log(superheroes[i]);
}
```

하지만, 배열의 forEach 함수를 사용하면 다음과 같이 구현 할 수 있다.

```javascript
const superheroes = ['아이언맨', '캡틴 아메리카', '토르', '닥터 스트레인지'];

superheroes.forEach(hero => {
  console.log(hero);
});
```

`forEach` 함수의 파라미터로는, 각 원소에 대하여 처리하고 싶은 코드를 함수로 넣어준다. 이 함수의 파라미터 hero는 각 원소를 가르키게 된다.

이렇게 함수형태의 파라미터를 전달하는 것을 `콜백함수` 라고 부른다. 함수를 등록해주면, `forEach` 가 실행을 해주는 것이다.