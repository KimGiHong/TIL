# WebStorage란?
웹 개발을 하다보면 간단한 애플리케이션의 데이터를 어딘가에 저장해야 할 일이 생긴다. 보통 이럴 때 DB 서버나 클라우드 플랫폼에 데이터를 저장하는 경우가 많을 것이다.  

하지만 저장해야할 데이터가 중요하지 않거나, 유시로디도 무방할 데이터라면 서버 단에 데이터를 저장하는 것이 낭비일 수도 있다.  

> 그럴때 클라이언트 단, 즉 브라우저 상에 데이터를 저장할 수 있는 웹 스토리지에 저장을 한다.  

### 웹 스토리지는 아래와 같은 특징을 갖는다.
1. 서버에 전송되지 않으므로 서버에 부담이 가지 않는다.  
2. 키(Key)와 값(Value)의 쌍 형태로 데이터를 저장한다.  
3. 대략 5MB까지의 데이터를 저장할 수 있다.  

# WebStorage의 2가지 종류
## 1. localStorage(영구 저장소)
- **반영구적 데이터 보관**  
    - 브라우저를 종료하여도 데이터 유지.  
    - 새로고침을 하여도 살아있다.  
- **동일한** 컴퓨터, **동일한** 브라우저내에서만 유지된다.  
    - firefox, chrome이 서로 `localStorage`가 공유되죈 않는다.  
    - 크럼을 켜서 네이버창을 3개 띄우면 모두 같은 `localStorage`를 공유한다.  

> 도메인이 다른 경우 로컬 스토리지에 접근할 수 없다. 예를 들어 www.google.com에서 로컬 스토리지에 저장한 데이터를 www.ieeexplore.ieee.org에서 접근할 수 없는 것과 같다.

* JS를 이용한 localStorage 접근
```javascript
localStorage.setItem('item1',10);
localStorage.setItem('item2','new item);
localStorage.setItem('item3',0.543534);

console.log(localStorage.getItem('item1'));
console.log(localStorage.getItem('item2'));
console.log(localStorage.getItem('item3'));
```

## 2. sessionStorage(임시 저장소)
- 데이터 **영구 보관** X.  
    - 세션 종료시 데이터 자동 제거.  
- 탭마다 개별적으로 데이터 저장.  
    - 크롬을 켜서 네이버창을 3개 띄우면 각각 다른 `sessionStorage`정보를 공유한다.  

> 같은 도메인이라도 세션이 다르면 데이터에 접근할 수 없다.  

* JS를 이용한 sessionStorage 접근
```javascript
localStorage.setItem('item1', 10);
localStorage.setItem('item2', 'new item');
localStorage.setItem('item3', 0.543534);
```

# 기본 API
**WebStorage는 `{key: value}` 형태로 저장한다.**  

WebStorage를 사용할때도 이를 감안하여 코드작성이 필요하다.  

```javascript
// 키에 데이터 쓰기
localStorage.setItem("key", value);

// 키로 부터 데이터 읽기
localStorage.getItem("key")

// 키의 데이터 삭제
localStorage.clear();

// 저장된 키/값 쌍의 개수
localStorage.length;
```

> 💥 `sessionStorage` 에 저장한다면 상단 코드의 `localStorage` 를 `sessionStorage` 로 바꾸면 된다.

# 주의사항
WebStorage에 무언가 저장할때 무조건 **문자열 형태**로 저장해야 한다.  

```javascript
localStorage.setItem('json', JSON.stringify({a: 1, b: 2})) // 저장

console.log(JSON.parse(localStorage.getItem('json'))) // {a: 1, b: 2} 출력
```

`json`을 키로, `{a: 1, b: 2}` 객체를 value로 저장하는 과정이다.  

> `JSON.stringfy()`함수를 사용해서 저장한다.

## localStorage는 자동 로그인 저장, sessionStorage는 입력 폼 정보 저장 및 비 로그인 장바구니 같은 예시들이 있다.