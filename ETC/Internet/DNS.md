# DNS 란?

* 도메인 네임 시스템( Domain Name System, DNS )은 호스트의 도메인네임 (www.example.com)을 네트워크 주소(192.168.1.0)로 변환하거나, 그 반대의 역할을 수행하는 시스템이다.

## DNS 서비스 유형

1. 신뢰할 수 있는 DNS
> * 개발자가 퍼블릭 DNS 이름을 관리하는데 사용하는 업데이트 매커니즘을 제공함.
> * 이를 통해 DNS 쿼리에 응답하여 도메인 이름을 IP 주소로 변환한다.
> * 신뢰할 수 있는 DNS는 도메인에 대해 최종 권한이 있다.
> * 재귀적 DNS 서버에 IP 주소 정보가 담긴 답을 제공할 책임이 있다.

2. 재귀적 DNS
> * 보통 클라이언트는 신뢰할 수 있는 DNS 서비스에 직접 쿼리를 수행하지 않는다.
> * 재귀적 DNS 서비스는 호텔 컨시어지와 같은 역할을 한다.
> * 일정 기간 동안 캐시된 또는 저장된 DNS 레퍼런스를 가지고 있는 경우, 소스 또는 IP 정보를 제공하여 DNS 쿼리에 답을 하거나, 해당 정보를 찾기 위해 쿼리를 하나 이상의 신뢰할 수 있는 DNS 서버에 전달한다.

## DNS 동작 원리

![image](https://user-images.githubusercontent.com/68697807/130890817-d8adfb95-f82d-43f8-aad3-7786e1df1ea2.png)

1. 웹 브라우저에 www.naver.com을 입력하면 먼저 Local DNS에게 "www.naver.com"이라는 hostname에 대한 IP 주소를 질의하하여 Local DNS에 없으면 다른 DNS name 서버 정보를 받음 `Root DNS 정보를 전달 받음`
2. Root DNS 서버에 "www.naver.com" 질의
3. Root DNS 서버로부터 "com 도메인"을 관리하는 TLD ( Top-Level Domain )이름 서버 정보를 전달 받음.
4. TLD에 "www.naver.com" 질의
5. TLD에서 "naver.com" 관리하는 DNS 정보 전달함
6. "naver.com" 도메인을 관리하는 DNS 서버에 "www.naver.com" 호스트네임에 대한 IP 주소 질의
7. Local DNS 서버에게 "응! www.naver.com에 대한 IP 주소는 222.122.195.6"을 응답한다.
8. Local DNS는 www.naver.com에 대한 IP 주소를 캐싱을 하고 IP 주소 정보 전달함

> * Recursive Query: Local DNS 서버가 여러 DNS 서버를 차례대로 ( Root DNS 서버 -> com DNS 서버 -> naver.com DNS 서버 ) 질의해서 답을 찾아가는 과정이라고 함.