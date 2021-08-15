# HTTP란?
대량의 정보가 흐르는 곳이라면 언제나 효율적인 교류를 위한 규칙이 존재한다.
예를들어 주식시장에서 거래를 하고 싶다면 이름, 계좌, 거래일자, 금액 등 정해진 규칙을 지켜 거래를 작성해야 한다. 규칙을 지켜야 사는 사람, 파는 사람 모두 효율적인 거래를 성사할 수 있다.

> `HTTP`란 한마디로 **HTML** 문서를 주고 받는데 쓰이는 통신프로토콜이며, **TCP**와 **UDP**를 사용하여 통신하며 80번 포트를 사용하는 통신프로토콜이다.

* 통신프로토콜 : 통신규약이라고도 하며 컴퓨터나 원거리 통신 장비 사이에서 메세지를 주고 받는 양식과 규칙의 체계

# HTTP특징
* HTTP 메세지는 **서버와 클라이언트에 의해 해석**된다.
* TCP/IP 를 이용하는 **응용프로토콜** 이다.
* HTTP는 연결상태를 유지하지 않는 **비연결성 프로토콜**이다. 클라이언트가 이전에 요청한 내용을 기억하고 있지 않는다.
* 비연결성의 단점을 해결하기 위해 **Cookie 와 Session**이 등장했다.
* **도메인 + 자원위치(URL), 도메인 + 자원의 식별자(URI)**를 통해서 요청을 하고, 서버가 요청에 따른 HTML 문서응답을 해준다.

# HTTP 통신과정(요청과 응답)

① 클라이언트(사용자)가 서버에 HTTP Request (요청)을 한다.  
② 서버가 사용자의 요청을 받고 HTTP Response (응답)을 한다.

## 1. HTTP Request(요청) 메세지
**요청**은 웹브라우저의 **URL**을 통해 어느 웹사이트(도메인)의 어느 경로에 있는 페이지를 요청할지 나타내는 행위이다. 요청 메세지의 세부사항은 아래와 같다.

```
Request-Line
*(( general-header | request-header | entity-header ) CRLF)
CRLF -> 줄바꿈
[ message-body ]
```

### 1. Request-Line
**Request-Line**, URL정보, 요청방식(Method),HTTP 버전정보제공의 규칙이다.

### 2. *(( general-header | request-header | entity-header ) CRLF)
**헤더 정보**, 헤더에는 요청하는 클라이언트 PC, 브라우저정보, 사용자언어환경, 쿠키 등의 다양한 클라이언트 환경에 대한 정보를 가지고 있다. 떄문에 헤더 영역에 존재하는 데이터는 보안에 취약하다.

### 3. [message-body]
**HTTP본문영역**, 주로 클라이언트가 입력한 데이터를 저장하는 영역이다.  
입력폼에 입력한 각종 데이터가 Method 방식에 따라 서버로 전달할 때 보안이 강화된 방식으로 message-body에 넣어 전달한다.

# 2. HTTP Response(응답) 메시지
**응답**은 HTTP Request 를 통해 요청된 정보에 대해 웹서버가 클라이언트에 보내는 응답형식 및 결과를 나타낸다.

```
Status-Line
*(( general-header | response-header | entity-header ) CRLF)
CRLF -> 줄바꿈
[ message-body ]
```

### 1. Status-Line
**응답 상태정보 표시 라인, HTTP버전정보 와 세자리 숫자값(200)과 상태코드 값을 통해 응답결과 및 상태정보를 나타낸다.

### 2. 응답 헤더정보 제공
**헤더정보**, 각종 서버 및 웹사이트 관련 환경정보를 제공한다.

### 3. [message-body]
**HTTP 본문영역**, 주로 서버에서 사용자에게 전달되는 HTML 소스 및 포함된 데이터를 저자하는 영역이다.

# HTTP Method
`Method`는 클라이언트가 웹서버에게 사용자의 요청의 목적/종류를 알리는 수단이다.
* GET: 정보 검색  
ex) 게시판 리스트 불러오기
* POST: 실행 / 저장  
ex) 회원가입 / 로그인
* PUT: 전체 수정  
ex) 회원정보 전체 수정
* DELETE: 삭제  
ex) 회원정보 삭제
* PATCH: 일부 수정  
ex) 회원정보 일부 수정(Update에 가깝게 쓰이고 있음)
* OPTIONS: 시스템에서 지원하는 메소드 확인

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
# HTTP Header
1. General header
요청과 응답에 모두 적용되지만, 데이터와는 관련 X 헤더  
Date나 Connection(클라이언트와 서버 간의 연결에 대한 옵션) 등

2. Request header
요청하는 클라이언트의 대한 자세한 정보를 포함하는 헤더  
Host, User-Agent, Cookie 등

3. Response header
서버 자체에 대한 정보, 응답에 대한 부가적인 정보를 포함하는 헤더
Server, Allow, ETag, Access-Control-Allow-Origin 등

4. Entity header
컨텐츠의 길이나 MIME 타입과 같이 엔티티 바디에 대한 자세한 정보를 포함하는 헤더 Content-Type, Content-Length 처럼 엔티티(콘텐츠, 본문, 리소스) 관련 정보 등

# HTTP Content-type

**Content-type**은 헤더에 포함되는 속성으로 리소스의 미디어 타입을 나타낸다.
* Application/x-www-form-urlencoded: HTML Form 형태
* Application/json: JSON 형태 값
* multipart/form-data: 파일 첨부
* text/*: 단순 html,css,javascript 파일

Application/x-www-form-urlencoded 과 form-data 모두 폼데이터지만,  
x-www-form-urlencoded는 대용량 바이너리를 보내는데 비능률적이다.
