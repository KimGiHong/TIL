# Rendering 이란
쉽게 말한다면, 브라우저에 그림을 그리는 행위.   
정확히는 HTML 파일을 **파싱**하여, 이를 사용자가 바라보고 있는 화면에 보여주는 행위이다.

> parsing(파싱): 어떤 문장을 분석하거나 문법적 관계를 해석하는 행위

# Rendering Engine
각 부라우저는 각자만의 렌더링 엔진을 사용한다.
* firefox : `Gecko`
* safari : `Webkit`
* chrome : `Webkit`을 `Blink`로 개발하여 사용.

# Rendering 과정
## 1.DOM,CSSOM 생성
* 서버로부터 `HTML`,`CSS`를 받아 다운로드 한다.
* 다운받은 `HTML`,`CSS`는 단순한 **텍스트 파일**이다.
* 연산과 관리의 효율을 위해 다운 받은 것들을 `object model`로 만든다.
    * `HTML`로 **DOM**(Document Object Model) **Tree**를 만든다.
    * `CSS`로 **CSSOM**(CSS Object Model)를 만든다.

![DOM](https://user-images.githubusercontent.com/68697807/119508162-7a5df500-bdaa-11eb-9550-8f1113c72290.png)
> 좌: DOM Tree, 우: CSSOM

## 2.Render Tree 생성
![Render](https://user-images.githubusercontent.com/68697807/119508328-a24d5880-bdaa-11eb-9c2d-2d5a00fa2e34.png)
* **DOM Tree** 와 **CSSOM**을 이용해 `**Render Tree**`로 만든다.
* `**Render Tree**`에는 스타일 정보가 설정되어 있으며 **실제 화면에 표현되는 노드들로만** 구성된다.
    * `display: none`속성은 화면에 어떤 부분도 차지하지 않으므로, `Rendering Tree`에는 포함되지 않는다.

## 3. Layout 계산하기
![Layout](https://user-images.githubusercontent.com/68697807/119508727-f0faf280-bdaa-11eb-896e-6d075818f6a0.png)

* `Rendering Tree`의 노드들의 각각 스타일, 속성에 따라 **브라우저 내 어디에 위치할 건지** 계산한다.
* 모든 노드들이 `**ViewPort**`내에서 어느 위치에 있을건지 계산된다.
    * `**ViewPort**`란, 그려지는 브라우저의 크기 / 영역을 말한다.
    * 모바일 / PC 모두 브라우저의 크기가 모두 상이하므로, 뷰포트가 달라지면 다시 계산해야한다.

## 4. Paint 그리기

**Rendering Tree 요소들을 실제 화면에 픽셀단위로 변환한다.**
* 스타일이 복잡할수록 **페인팅에 걸리는 시간**도 늘어난다.
    * 예를 들어, 단색은 페인트하는 데 시간과 작업이 적게 필요한 반면, **그림자 효과**는 계산하고 렌더링하는데 **시간과 작업이 더 필요하다.**