# AJAX란?

* AJAX 란 비동기 자바스크립트와 XML  (Asynchronous JavaScript And XML) 을 말한다.
간단히 말해, 서버와 통신하기 위해 XMLHttpRequest 객체를 사용하는 것을 말한다.
JSON, XML, HTML 그리고 일반 텍스트 형식 등을 포함한 다양한 포맷을 주고 받을 수 있다.
AJAX 의 주된 특징은 페이지 전체를 리프레쉬 하지 않고서도 수행 되는 `"비동기성"`이다. 
이러한 비동기성을 통해 사용자의 Event가 있으면 전체 페이지가 아닌 일부분만을 업데이트 할 수 있게 해준다.

AJAX 의 주요 두가지 특징은 이와 같은 작업을 할 수 있게 해준다.
* 페이지 새로고침 없이 서버에 요청
* 서버로부터 데이터를 받고 작업을 수행

## 1. HTTP request 만드는 방법

JavaScript 를 이용하여 서버로 보내는 [HTTP](HTTP.md) request를 만들기 위해서는 그에 맞는 기능을 제공하는 Object의 인스턴스가 필요하다. [XMLHttpRequest](XHR.md) 가 그러한 Object의 한 예이다.

서버에 요청(Request)을 하기에 앞서, 서버로 보낸 요청에 대한 응답을 받았을 때 어떤 동작을 할 것인지 정해야합니다. 위에서 생성한 httpRequest 의 `onreadystatechange` property에 특정 함수(`nameOfTheFunction`)를 할당하면 요청에 대한 상태가 변화할 때 특정 함수(`nameOfTheFunction`)가 불리게 됩니다.

```javascript
httpRequest.onreadystatechange = nameOfTheFunction;
```

주목할 사항으로는 위에서는 해당 함수를 수행하는 것이 아니라 단순하게 어떤 함수가 불릴 것인지만 지정한다는 점입니다. 단순하게 그 함수를 지정하는 것이므로 그 함수로 어떠한 변수도 전달하지 않습니다. 또한 단순하게 함수를 연결하면 되기 때문에 아래와 같이 JavaScript에서 사용되는 ["임의 함수(anonymous functions)"](AF.md)방법으로 직접적인 함수 본체를 기입해도 됩니다.

```javascript
httpRequest.onreadystatechange = function(){
    // 서버의 응답에 따른 로직을 여기에 작성합니다.
};
```

위와 같이 서버로 부터 응답을 받은 후의 동작을 결정 한 뒤에, 요청을 합니다. 아래와 같이 HTTP request 객체의 `open()`과 `send()`를 사용하면 요청을 할 수 있습니다.

```javascript
httpRequest.open('GET', 'http://www.example.org/some.file', true);
httpRequest.send(null);
```

`open()` 메소드의 파라미터

* 첫번째 파라미터는 HTTP 요구 방식(request method) ─ GET, POST, HEAD 중의 하나이거나 당신의 서버에서 지원하는 다른 방식 ─ 입니다. 이 파라미터는 HTTP 표준에 따라 모두 대문자로 표기해야합니다. 그렇지 않으면 (파이어폭스와 같은) 특정 브라우저는 이 요구를 처리하지 않을 수도 있습니다. HTTP 요구 방식의 보다 자세한 정보는 W3C 명세를 참고하기 바랍니다.
* 두번째 파라미터는 요구하고자하는 URL 입니다. 보안상의 이유로 서드 파티 도메인 상의 URL은 기본적으로 호출할 수 없습니다. 요구하는 모든 페이지에 정확한 도메인 네임을 사용하십시오. 그렇지 않으면 open() 메소드를 호출할 때 'permission denied' 에러가 발생할 수 있습니다. 일반적인 오류는 당신의 사이트에 domain.tld 와 같은 형태로 접근하는 것 입니다. 이러한 경우 www.domain.tld 와 같은 형태로 페이지를 요구하기 바랍니다. 만약 다른 도메인으로 요청을 보내고 싶다면 [HTTP 접근 제어 (CORS)](CORS.md) 를 참고하기 바랍니다.
* 세번째 파라미터(생략 가능)는 요구가 비동기식(Asynchronous)으로 수행될 지를 결정합니다. 만약 이 파라미터가 `true`(기본값) 으로 설정된 경우에는 자바스크립트 함수가 지속적으로 수행될 수 있어 서버로부터 응답을 받기 전에도 유저와 페이지의 상호작용이 계속 진행됩니다. 이것이 AJAX 의 첫번째 A (Asynchronous : 비동기성) 입니다.
    * `false`로 설정된 경우 동기적으로 작동합니다. (`send()` 함수에서 서버로부터 응답이 올 때까지 기다림)

`send()` 메소드의 파라미터는 POST 방식으로 요구한 경우 서버로 보내고 싶은 어떠한 데이터라도 가능합니다. 데이터는 서버에서 쉽게 parse할 수 있는 형식(format)이어야 합니다. 예를 들자면 아래와 같습니다

```javascript
"name=value&anothername="+encodeURIComponent(myVar)+"&so=on"
```

만약 POST 형식으로 데이터를 보내려 한다면, 요청(request)에 MIME type을 먼저 설정 해야 합니다. 예를 들자면 `send()`를 호출 하기 전에 아래와 같은 형태로 send()로 보낼 쿼리를 이용해야 합니다.

```javascript
httpRequest.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded');
```

## 2. 서버 응답에 대한 처리

서버로 요청(request)을 보내기 전에, 위에서는 서버의 응답을 처리하기 위한 자바스크립트 함수의 이름을 지정했었습니다.
```javascript
httpRequest.onreadystatechange = nameOfTheFunction;
```

이 함수는 먼저 해당 함수에서는 요구의 상태값을 검사할 필요가 있습니다. 만약 상태값이 XMLHttpRequest.DONE (상수 4로 정의되어 있습니다.) 라면, 서버로부터 모든 응답을 받았으며 이를 처리할 준비가 되었다는 것을 뜻합니다.

```javascript
if (httpRequest.readyState === XMLHttpRequest.DONE) {
    // 이상 없음, 응답 받았음
} else {
    // 아직 준비되지 않음
}
```
`readyState` 가 가질 수 있는 모든 값의 목록은 [XMLHTTPRequest.readyState](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/readyState)에 작성되어있으며 아래와 같다.

* 0 (uninitialized) - (request가 초기화되지 않음)
* 1 (loading) - (서버와의 연결이 성사됨)
* 2 (loaded) - (서버가 request를 받음)
* 3 (interactive) - (request(요청)을 처리하는 중)
* 4 (complete) - (request에 대한 처리가 끝났으며 응답할 준비가 완료됨)

그 다음에는 [HTTP 응답 상태 코드](https://developer.mozilla.org/ko/docs/Web/HTTP/Status)를 검사해야한다.아래 예제에서는 AJAX 요청이 정상적으로 처리되었는지 아닌지만을 검사하기 위해 응답 코드가 200 OK 인지 검사하는 예제입니다.

```javascript
if (httpRequest.status === 200) {
    // 이상 없음!
} else {
    // 요구를 처리하는 과정에서 문제가 발생되었음
    // 예를 들어 응답 상태 코드는 404 (Not Found) 이거나
    // 혹은 500 (Internal Server Error) 이 될 수 있음
}
```

이제 요구와 그에 대한 응답에 대한 상태 코드를 검사했으므로, 서버에서 받은 데이터를 통해 원하는 작업을 수행할 수 있다. 그리고 응답 데이터에 접근하기 위한 옵션이 2가지 있다

* `http_request.responseText` – 서버의 응답을 텍스트 문자열로 반환할 것이다.
* `http_request.responseXML` – 서버의 응답을 XMLDocument 객체로 반환하며 당신은 자바스크립트의 DOM 함수들을 통해 이 객체를 다룰 수 있을 것이다.

위의 단계는 비동기식 요구(asynchronous request)를 사용했을 경우에 대한 설명입니다(즉, `open()`의 세번째 변수가 생략되었거나 `true` 일 경우). 동기식(Synchronous) 방법을 사용한다면 함수(`nameOfTheFunction`)를 명시할 필요 없이 `send()` 호출에 의해 반환되는 data를 바로 사용 할 수 있습니다. 그러나 이는 스크립트가 `send()`를 호출할 때 멈춰지며 서버의 응답이 완료 될 때까지 기다리기 때문에 나쁜 UX를 제공하게 합니다.