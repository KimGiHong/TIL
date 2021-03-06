# 도메인네임(Domain Name)이란?

* `Domain Name`은 웹사이트의 주소, 즉 웹사이트를 찾기 위한 고유한 **문자형 주소체계**를 말한다.
* https://naver.com에서 **https**는 통신방식을 말하며 **www**는 호스트이며 **naver.com**이 실제 도메인 주소이다.
* 통신망 환경에서 컴퓨터나 통신장비간 통신에 최적화된 주소체께는 **IP Address**이다. 하지만 이는 숫자로 이루어져 사람이 기억하기 힘들다. 이런 단점을 보완하기 위해 등장한 것이 문자형 주소 체계인 **도메인 네임**이다.
* 문자주소체계인 도메인 주소는 **상호맵핑되는 구조**를 가진다.(IP Address <-> Domain Name)
* 도메인만 알면 자동으로 통신과정 중 IP로 변한되어 컴퓨터간 통신할 수 있게 자동처리 해주는 서비스를 **DNS(Domain Name Service)** 라고 한다.

# 도메인 체계
![domain](https://user-images.githubusercontent.com/68697807/121176430-2a495d00-c897-11eb-9d31-667fccd2870d.gif)

* 도메인은 `.`또는 `루트(root)` 라고 불리는 도메인 이하에 위의 그림과 같이 역트리 구조로 구성되어 있다.
* 루트 도메인 바로 아래의 단계를 1단계 도메인 또는 최상위 도메인(TLD, Top Level Domain)이라고 부르며, 그 다음 단계를 2단계 도메인(SLD, Second Level Domain)이라고 부른다.

# 도메인 종류
* 도메인에는 `국가 도메인(ccTLD, country code ")과 일반도메인(gTLD, generic ")`이 있다.
* **국가 도메인**은 인터넷 상에서 국가를 나타내는 도메인으로 `.kr , .jp , .cn , .us` 등 영문으로 구성된 영문 국가 도메인이 있다. 또한 `.한국 , .중국 , .러시아 , .이집트` 처럼 자국어 국가 도메인이 있다.
* **일반 도메인**은 `.com(회사) , .net(네트워크 관련기관) , .org(비영리기관) , .biz(사업)`등 등록인의 특성에 따라 사용할 수 있는 도메인이다.
<br>

### 1. 국가 최상위 도메인
> 인터넷 상에서 국가를 나타내는 영문 및 자국어 도메인
* 2자리 영문 국가코드 또는 자국어 국가코드로 이뤄짐

### 2. 일반 최상위 도메인
> 조직, 목적, 분류 등 명칭을 영문약자로 표현한 최상위 도메인
* 영문은 3자리 이상, 영문 외 다국어는 2자리 이상으로 이뤄짐