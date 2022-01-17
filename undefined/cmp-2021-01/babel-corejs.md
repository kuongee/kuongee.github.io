# babel과 corejs

현재 진행하고 있는 프로젝트를 띄워보니 화면이 아예 백화로 표시되는 문제가 발생했다.

에러 로그를 살펴보니 아래와 같은 로그가 남았다.



이전까지는 멀쩡하게 잘 사용하던 string의 replace 함수와 관련된 곳에서 문제가 생기고 있었다!?

그리고 로그를 잘 보면 babel, core-js와 관련되어 보여서 관련된 키워드로 찾아보았다.

이렇게 저렇게 검색을 해본 결과

Babel에서 사용하는 core-js의 버전이 맞지 않아서 발생하는 문제인 거 같다.

* [https://e2xist.tistory.com/741](https://e2xist.tistory.com/741)
* [https://avaiable.tistory.com/140](https://avaiable.tistory.com/140)

이것저것 알아보기

vue cli로 만든 프로젝트에서는 **@vue/cli-plugin-babel**로 babel 설정해주고 있음

* babel plugin for vue-cli
* **Babel 7** + babel-loader + @vue/babel-preset-app 을 기본으로 사용하고 있음
* babel.config.js에서 다른 Babel preset이나 plugin을 설정해서 사용할 수 있음

babel-polyfill (Babel 7.4.0 부터 deprecated)

[https://babeljs.io/docs/en/babel-polyfill](https://babeljs.io/docs/en/babel-polyfill)

* Babel은 ES6 문법의 코드를 ES5 환경에서 동작할 수 있게 Syntax 변환을 해줌 (컴파일 타임)\
  그러나 ES5에 존재하지 않는 ES6 메서드나 생성자들까지는 코드 변환으로는 해결하기 어렵기 때문에 polyfill을 사용해서 해결해야함\
  그래서 @babel/polyfill이 deprecated 되기 전에는 이 모듈을 사용하기도 했음
* polyfill은 전역 스코프에 추가&#x20;

[https://so-so.dev/web/you-dont-know-polyfill/](https://so-so.dev/web/you-dont-know-polyfill/)

[https://simsimjae.medium.com/개발을-하다보니-이런-에러가-생겨서-원인을-찾다가-폴리필-문제라는걸-깨닫고-정리합니다-217a207f8181](https://simsimjae.medium.com/%EA%B0%9C%EB%B0%9C%EC%9D%84-%ED%95%98%EB%8B%A4%EB%B3%B4%EB%8B%88-%EC%9D%B4%EB%9F%B0-%EC%97%90%EB%9F%AC%EA%B0%80-%EC%83%9D%EA%B2%A8%EC%84%9C-%EC%9B%90%EC%9D%B8%EC%9D%84-%EC%B0%BE%EB%8B%A4%EA%B0%80-%ED%8F%B4%EB%A6%AC%ED%95%84-%EB%AC%B8%EC%A0%9C%EB%9D%BC%EB%8A%94%EA%B1%B8-%EA%B9%A8%EB%8B%AB%EA%B3%A0-%EC%A0%95%EB%A6%AC%ED%95%A9%EB%8B%88%EB%8B%A4-217a207f8181)

[https://tech.kakao.com/2020/12/01/frontend-growth-02/](https://tech.kakao.com/2020/12/01/frontend-growth-02/)

[https://velog.io/@vnthf/corejs3로-대체하자-zok3p9aouy#그래서-core-js3는-어떻게](https://velog.io/@vnthf/corejs3%EB%A1%9C-%EB%8C%80%EC%B2%B4%ED%95%98%EC%9E%90-zok3p9aouy#%EA%B7%B8%EB%9E%98%EC%84%9C-core-js3%EB%8A%94-%EC%96%B4%EB%96%BB%EA%B2%8C)

[https://velog.io/@kwonh/Babel-%ED%8F%B4%EB%A6%AC%ED%95%84polyfill-babelpreset-env](https://velog.io/@kwonh/Babel-%ED%8F%B4%EB%A6%AC%ED%95%84polyfill-babelpreset-env)

core-js

* polyfill 모듈.....?
* Babel 7.4부터 core-js@3을 같이 사용\
  그런데 default가 core-js 2 이라서 문제가 생겼음\
