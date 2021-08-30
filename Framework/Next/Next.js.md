# Next.js

Next.js는 React의 SSR( Server Side Rendering )을 쉽게 구현할 수 있게 도와주는 **Vercel**이란 팀에서 만든 간단한 프레임 워크이다.

# Next.js의 주요기능

## Server-Side Rendering
React에서도 써드파티 라이브러리 내장 기능을 사용해서 SSR을 구현할 수 있지만, Next.js를 사용한다면 별다른 설정없이 **SSR**을 구현할 수 있다. 

## File Based Routing
너무나도 간단한 라우팅이다, 가장 두드러지면서도 쉽게 마주칠 수 있는 장점이라고 생각한다.  
react-router-dom의 Router 등에 의지하지 않고도 pages 폴더에 파일을 만드는 것 만으로도 해당 라우팅으로 파일이 자동 세팅된다.

## Hot Code Reloading
디스크에 어떤 변화가 감지될 때 페이지를 리로드한다.

## Single File Components
styled-jsx를 사용할 수 있다.

## Automatic Code Splitting
페이지를 로딩하면 해당 페이지에 필요한 자바스크립트를 로드한다.

## Prefetching
Link 컴포넌트는 백그라운드에서 자동으로 페이지 리소스를 prefetch한다.

## TypeScript Support