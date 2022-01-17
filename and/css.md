# CSS

## CSS (Cascading Style Sheets)

* HTML document의 스타일을 표현하고 어떻게 HTML element들이 보여야하는지 정의(스타일링)

### CSS Transition <a href="#html-and-css-csstransition" id="html-and-css-csstransition"></a>

* 주어진 시간동안 속성 값이 부드럽게 변할 수 있게 함\

  * 동작하지 않는 브라우저도 있음
* CSS에서 transition이라는 property를 사용함\

  * JavaScript랑 같이 사용해서 동작시킬 수도 있음

**Reference**

* [https://zellwk.com/blog/css-transitions/](https://zellwk.com/blog/css-transitions/)

### React의 여러 컴포넌트 스타일링 방식 <a href="#html-and-css-react" id="html-and-css-react"></a>

[https://velog.io/@velopert/react-component-styling](https://velog.io/@velopert/react-component-styling)

#### 1. CSS Modules <a href="#html-and-css-1.cssmodules" id="html-and-css-1.cssmodules"></a>

* **Scoped locally**
  * Default로 class 이름/selector 이름이 local 변수처럼 사용될 수 있게 함
  * Globally Unique 한 css rule 이 되게 함
    * Unique한 global 이름을 만들어내기 때문에 여러 CSS Module을 사용할 때 같은 이름을 사용해도 문제가 없음
  * 이렇게 해서 스타일이 겹치지 않게
* 그냥 .css file 일뿐
  * 하나의 CSS 파일이 CSS Module\
    ![incomplete](https://www.javascriptstuff.com/static/css-modules-diagram-incomplete-f2ff456c36a0f2ca41509827cc937eb2-2dcac.png)![css modules diagram incomplete](https://www.javascriptstuff.com/static/css-modules-diagram-incomplete-example-1457ccc0c0d6fc2bac2652cea6ad2940-2dcac.png)\

  * [https://www.javascriptstuff.com/what-are-css-modules/](https://www.javascriptstuff.com/what-are-css-modules/)
* CSS Modules **rewrite class names**, but they don't touch tag names.
  * tag 이름을 그대로 둔다면, CSS rule이 전체 app에 globally 적용될 수 있기 때문에 class 이름을 항상 넣어주는게 좋음
* Webpack을 사용한다면 CSS Modules compiler가 이미 있음 → Javascript 모듈 안에서 CSS를 불러올 수 있게 됨\

  * css-loader
  * build 단계에서 import한 css 파일에서 정의한 class 이름을 찾아서 새로운 html, css 파일을 생성해버림
* **궁금한 점**\
  ****
  * CSS Modules를 쓰는 이유는?
    * CSS를 모듈처럼 JS에 적용해서 쓰겠다\

  * CSS Rule이 globally 적용된다는게 무슨 뜻?
    * CSS는 원래부터 global 특성
      * [https://css-tricks.com/regarding-css-global-scope/](https://css-tricks.com/regarding-css-global-scope/)\

    * css selector는 global scope 안에 존재하고 있음
      * [https://medium.com/seek-blog/the-end-of-global-css-90d2a4a06284](https://medium.com/seek-blog/the-end-of-global-css-90d2a4a06284)\


**Reference**

* CSS Modules 예제
  * [https://www.javascriptstuff.com/css-modules-by-example/](https://www.javascriptstuff.com/css-modules-by-example/)
* [https://css-tricks.com/css-modules-part-1-need/](https://css-tricks.com/css-modules-part-1-need/)
* [https://www.javascriptstuff.com/what-are-css-modules/](https://www.javascriptstuff.com/what-are-css-modules/)\

  * [https://glenmaddern.com/articles/css-modules](https://glenmaddern.com/articles/css-modules)
* [JavaScript Module 관련](http://confluence.score/display/\~jeesoo.min/JavaScript)

#### 2. Styled Component <a href="#html-and-css-2.styledcomponent" id="html-and-css-2.styledcomponent"></a>

* React component를 styling 할 수 있게 함
* Style이 적용된 component 자체를 정의해서 사용\

  * CSS rule을 쓸 수 있음
  * 특히 React에서 잘 쓸 수 있게 해주는 거 같음

**Reference**

* Official Documentation\

  * [https://www.styled-components.com/docs/basics#motivation](https://www.styled-components.com/docs/basics#motivation)
    * babel이랑 쓰기를 추천하고 있음
