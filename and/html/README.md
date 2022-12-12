---
description: HTML과 관련된 기술들을 정리합니다.
---

# HTML

## HTML

* 웹 페이지를 만드는 표준 언어
* 태그를 이용해서 컨텐츠에 구조를 정의, 브라우저는 태그를 이용해서 페이지 내용을 그림(render)
  * HTML은 컨텐츠를 어떻게 보여줄지 구조화, 스타일링은 CSS

**Reference**

* HTML 기본 사용법
  * [https://www.w3schools.com/html/html\_intro.asp](https://www.w3schools.com/html/html\_intro.asp)
  * [https://developer.mozilla.org/ko/docs/Learn/HTML](https://developer.mozilla.org/ko/docs/Learn/HTML)
* **(다시 살펴보기)** 브라우저에서 어떻게 HTML을 읽고 Rendering 하는지에 대해
  * [How Browser render a website](https://www.youtube.com/watch?v=SmE4OwHztCc)
  * [https://www.html5rocks.com/en/tutorials/internals/howbrowserswork/](https://www.html5rocks.com/en/tutorials/internals/howbrowserswork/)

**DOM (Document Object Model)**

* 웹 페이지가 로드되면, 브라우저는 페이지의 DOM을 생성
* Object들의 트리 형태로 구성
* 여기에다가 JavaScript가 더해지면 각 객체들을 제어해서 dynamic HTML을 만들 수 있는 것\
  \
  ![DOM HTML tree](https://www.w3schools.com/js/pic\_htmltree.gif)\
  \

* HTML 원소들은 DOM에서 object로 정의
  * HTML 원소들의 내용을 바꿀 수도 있고 원소들에 action(찾고 더하고 삭제 등)을 주는 method를 적용할 수도 있음

**Reference**

* HTML DOM 소개
  * [https://www.w3schools.com/js/js\_htmldom.asp](https://www.w3schools.com/js/js\_htmldom.asp)

## HTML5

* 이전보다 User Experience를 향상시킴
*   html 문서 위에 HTML5임을 선언



    ```markup
    <!DOCTYPE HTML>
    ```
* &#x20;텍스트 또는 하이퍼링크 뿐만 아니라 멀티미디어 등 다양하게 제공 가능
  * 오디오, 비디오, 위치정보 등
  * local storage도 지원 - HTML Web Storage
    * Web application은 User의 브라우저에 데이터를 저장할 수 있음
      * 서버로 데이터를 전송할 필요가 없고 더 안전하고 많은 데이터를 저장할 수 있게 됨
      * HTML5 이전에는 cookie에 의존해서 상태 정보를 유지했었음
    * 설명 및 기본 사용법
      * [https://www.w3schools.com/HTML/html5\_webstorage.asp](https://www.w3schools.com/HTML/html5\_webstorage.asp)
      * [https://unikys.tistory.com/352](https://unikys.tistory.com/352)

**Reference**

* HTML vs. HTML5
  * [https://www.keycdn.com/blog/html-vs-html5](https://www.keycdn.com/blog/html-vs-html5)
* [https://webclub.tistory.com/491](https://webclub.tistory.com/491)
* 해당 기능을 브라우저에서 지원하는지 확인해볼 수 있는 사이트
  * [caniuse.com](http://caniuse.com)
* 해당 기능이 브라우저에서 지원되는지 확인하는 자바스크립트 코드
  * [https://modernizr.com/](https://modernizr.com/)
