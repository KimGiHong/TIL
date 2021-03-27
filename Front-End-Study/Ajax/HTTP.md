# HTTP란?

* HTTP는 Hyper Text Transfer Protocol 의 약자이다.
* 컴퓨터들끼리 HTML 파일을 주고 받을 수 있도록 하는 소통방식 또는 약속, 규약

## HTTP의 두 가지 특징

1. Request & Response : 통신의 핵심
1. stateless : 상태 없음

> 각각의 HTTP 통신 (요청/응답)은 독립적 이기 떄문에 과거의 통신 (요청/응답)에 대한 내용을 전혀 알지 못한다.
`따라서 매 통신마다 필요한 모든 정보를 담아서 요청을 보내야 한다.`
따라서, 만일 여러번의 통신 (요청/응답)의 진행과정에서 연속된 데이터 처리가 필요한 경우 (`ex. 온라인 쇼핑몰에서 로그인 후 장바구니 기능`)를 위해 로그인 토큰 또는 브라우저의 쿠키, 세션, 로컬스토리지 같은 기술이 필요에 의해 만들어졌다.

## Request / Response

#### Request 

* HTTP 요청은 프론트엔드(클라이언트)에서 백엔드(서버)에 일(데이터 처리)을 시작하게 하기 위해 보내는 메세지
* 크게 세 부분으로 구성 되있다.

1. Start Line : 요청의 첫 번째 줄. 세 부분으로 구성되있다.

```
1. HTTP Method : 해당 요청이 의도한 액션을 정의하는 부분. 주로 GET, POST, DELETE가 많이 쓰인다.
2. Request target : 해당 request가 전송되는 목표 url
3. HTTP Version : 말 그대로 사용되는 HTTP 버전
```

2. Headers : 해당 요청에 대한 추가 정보(메타 데이터)를 담고있는 부분이다.

```
Key : Value 값으로 되어있다. (Javascript의 객체, Python의 딕셔너리 형태라고 보면 된다)
자주 사용되는 Headers 의 정보에는 다음이 있다.

Headers: {
    Host : 요청을 보내는 목표(타겟)의 주소. 즉, 요청을 보내는 웹사이트 기본 주소 된다.
    (ex. www.apple.co.kr)
    User-Agent : 요청을 보내는 클라이언트의 대한 정보 (ex. Chrome, firefox, safari, explorer)
    Content-Type : 해당 요청이 보내는 메세지 body의 타입 (ex. application/json)
    Content-Length : body 내용의 길이
    Authorization : 회원의 인증/인가를 처리하기 위해 로그인 토큰을 Authorization 에 담는다.
}
```

3. Body : 해당 요청의 실제 내용. 주로 Body를 사용하는 메소드 POST다.
```
Body: {
    "user_email" : "jun.choi@gmail.com"
    "user_password" : "wecode"
}
```

#### Response

1. Status Line : 응답의 상태 줄이다. 응답은 요청에 대한 처리상태를 클라이언트에게 알려주시면서 내용을 시작

```
1. HTTP Version : 요청의 HTTP버전과 동일
2. Status Code : 응답 메세지의 상태 코드
3. Status Text : 응답 메세지의 상태를 간략하게 설명해주는 텍스트

HTTP /1.1 404 Not Found
해석 : HTTP 1.1 버전으로 응답하고 있는데, 프론트엔드에서 보낸 요청(ex. 로그인 시도)에 대해서
        유저의 정보를 찾을 수 없기 때문에(Not Found) 404 상태 메세지를 보낸다.

HTTP 1.1 200 SUCCESS
해석 : HTTP 1.1 버전으로 응답하고 있는데, 프론트엔드에서 보낸 요청에 대해서 성공했기 떄문에 200 메세지를 보낸다.
```

2. Headers

* 요청의 헤더가 동일
* 응답의 추가 정보(메타 데이터)를 담고 있는 부분
* 응답에서만 사용되는 헤더의 정보들이 있다. (ex. 요청하는 브라우저가 담긴 User-Agent 대신, Server 헤더가 사용된다.)

3. Body

* Body: 요청의 Body와 일반적으로 동일하다. 요청의 메소드에 따라 Body가 항상 존재하지 않듯이. 응답도 응답의 형태에 따라 데이터를 전송할 필요가 없는 경우엔 Body가 없을 수도 있다. 가장 많이 사용되는 Body 의 데이터 타입은 JSON(JavaScript Object Notation) 이다.

```javascript
ex) 로그인 요청에 대해 성공했을 때 응답의 내용
Body: {
	"message": "SUCCESS"
	"token": "kldiduajsadm@9df0asmzm" (암호화된 유저의 정보)
}
```

## Response Status Codes

> 실제 프로젝트를 진행할 때 가장 많이 보게될 응답의 상태 코드

#### 200: OK
* 가장 자주 보게되는 Status Code
* 문제없이 요청에 대한 처리가 백엔드 서버에서 이루어지고 나서 오는 응답코드
* 우리는 모두 200 OK 를 원한다

#### 201: Created
* 무언가가 잘 생성되었을 때에(Successfully Created) 오는 Status Code
* 대게 POST 메소드의 요청에 따라 백엔드 서버에 데이터가 잘 생성 또는 수정 되었을 때에 보내는 코드

#### 400: Bad Request
* 해당 요청이 잘못되었을 때 보내는 Status Code
* 주로 요청의 Body에 보내는 내용이 잘못되었을 때 사용되는 코드
ex) 전화번호를 보내야 하는데 숫자가 아닌 문자열의 주소가 대신 Body에 담겼을 경우

#### 401: Unauthorized
* 유저가 해당 요청을 진행하려면 먼저 로그인을 하거나 회원가입이 필요하다는 의미
ex) wish list, 좋아요 기능은 회원이 아니면 요청을 보낼 수 없음

#### 403: Forbidden
* 유저가 해당 요청에 대한 권한이 없다는 뜻
* 접근 불가능한 정보에 접근했을 경우
ex) 오직 유료회원만 접근할 수 있는 데이터를 요청 했을 때

#### 404: Not Found
* 요청된 URI 가 존재하지 않는다는 의미

#### 500: Internal Server Error
* 서버에서 에러가 났을 때의 Status Code
* API 개발을 하는 백엔드 개발자들이 싫어하는 코드 ~~(프론트는 내 잘못 아니라는 것을 알 수 있는 코드)~~