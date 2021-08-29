# 면접 질문 답 정리 및 예상 질문 공부

## HTML, CSS

* innerHTML

  | 장점 | 단점 |
  | :--- | :--- |
  | DOM 조작 방식에 비해 빠르고 간편하다. | XSS공격에 취약점이 있기 때문에 사용자로 부터 입력받은 콘텐츠\(untrusted data: 댓글, 사용자 이름 등\)를 추가할 때 주의하여야 한다. |
  | 간편하게 문자열로 정의한 여러 요소를 DOM에 추가할 수 있다. |  |

  * [https://gist.github.com/caike/35522c3da161d29fc2ce](https://gist.github.com/caike/35522c3da161d29fc2ce)
  * The following code will not trigger an alert. `target.innerHTML = "<script> alert('XSS Attack'); </script>";`

    The following code will trigger an alert. `target.innerHTML = "<img src=x onerror=\"alert('XSS Attack')\" >";`

  * [https://developer.mozilla.org/en-US/docs/Web/API/Element/innerHTML](https://developer.mozilla.org/en-US/docs/Web/API/Element/innerHTML)

* DOM
  * 문서에 접근하고 관리할 수 있는 API로 볼 수 있다. 문서를 브라우저가 이해할 수 있도록 메모리에 올려야 하는데 웹 문서를 브라우저가 이해할 수 있는 구조록 구성하는데 DOM이라고 한다. 요소들이 각각의 객체가 되고 객체들의 구조는 트리 형태이다.

![](../.gitbook/assets/image%20%2831%29.png)

* HTML 렌더링 과정
  * > **웹 브라우저의 HTML문서 렌더링 과정**

    **1. 불러오기**

    로더\(Loader\)가 서버로부터 전달 받는 리소스 스트림을 읽는 과정.

    읽으면서 어떤 파일인지, 데이터인지 파일을 다운로드할 것인지 등을 결정한다.

    **2. 파싱 \(Phasing\)**

    웹 엔진이 가지고 있는 HTML/XML 파서가 문서를 파싱해서 DOM Tree를 만든다.

    **3. 렌더링 트리 만들기**

    DOM Tree는 내용을 저장하는 트리로 자바스크립트에서 접근하는 DOM객체를 쓸 때 이용하는 것이고 별도로 그리기 위한 트리가 만들어져야 하는데 그것이 렌더링 트리다. \(그릴 때 필요없는 head, title, body태그등이 없음 + display:none 처럼 DOM에는 있지만 화면에서는 걸러내야할 것들을 걸러냄\)

    **4. CSS 결정**

    CSS는 선택자에 따라서 적용되는 태그가 다르기 때문에 모든 CSS 스타일을 분석해 태그에 스타일 규칙이 적용되게 결정한다.

    **5. 레이아웃**

    렌더링 트리에서 위치나 크기를 가지고 있지 않기 때문에 객체들에게 위치와 크기를 정해주는 과정을 레이아웃이라고 함.

    **6. 그리기**

    렌더링 트리를 탐색하면서 그리기.

    \* 참고로 렌더링 엔진은 가능하면 HTML문서가 파싱될 때까지 기다리지 않고, 배치와 그리기 과정을 시작한다.  
  
    출처: [https://jeong-pro.tistory.com/90](https://jeong-pro.tistory.com/90) \[기본기를 쌓는 정아마추어 코딩블로그\]

  *  렌더링 엔진은 HTML 문서를 파싱하고 "콘텐츠 트리" 내부에서 태그를 [DOM](http://www.html5rocks.com/en/tutorials/internals/howbrowserswork/) 노드로 변환한다. 그 다음 외부 CSS 파일과 함께 포함된 스타일 요소도 파싱한다. 스타일 정보와 HTML 표시 규칙은 "[렌더](http://www.html5rocks.com/en/tutorials/internals/howbrowserswork/) [트리](http://www.html5rocks.com/en/tutorials/internals/howbrowserswork/)"라고 부르는 또 다른 트리를 생성한다. [https://d2.naver.com/helloworld/59361](https://d2.naver.com/helloworld/59361)
  * HTMl 파싱 중 스크립트 태그를 만나는 순간부터는 이 스크립트를 로드하고 실행한다. 이 말은 스크립트 태그 뒤쪽에 있는 페이지의 요소들은 그려지지 못하고 앞쪽 스크립트의 로드/실행이 끝날 때까지 기다려야 한다.

![](../.gitbook/assets/image%20%2827%29.png)



* DOMContentLoaded와 load event 비교
  * **DOMContentLoaded**: 브라우저가 HTML 전부 로드되고 DOM 트리를 완성하는 즉시 발생한다. \(이미지, 스타일 등의 외부 자원들은 기다리지 않는다.\)
    * DOM이 준비되었기 때문에 DOM 노드에 접근이 가능
    * document 객체에서 실행
  * **load**: DOM 트리도 완성되고 외부 자원도 모두 불러오는 것이 끝났을 때 발생한다.
    * 이미지 크기, 스타일 적용 후 실제 요소의 크기 확인 등이 가능
    * window 객체에서 실행
  * **beforeunload/unload**: 사용자가 페이지를 떠날 때 발생한다.
    * beforeunload는 예시로 '정말 이 페이지를 나가시겠습니까?' 이런 체크를 할 때 사용할 수 있다.
    * window 객체에서 발생

## JavaScript

* Event Loop, Micro Task Queue
  * [https://ko.javascript.info/event-loop](https://ko.javascript.info/event-loop)
  * **더 정리**
* ES6에서 추가된 것들이 뭐가 있는지
  * const let 
  * string literal
  * spread operator
  * 화살표 함수
* Hoisting?
  * [https://github.com/kuongee/my-js/blob/kuongee/Frontend/JavaScript/hoisting.md](https://github.com/kuongee/my-js/blob/kuongee/Frontend/JavaScript/hoisting.md)
* const let var 비교
  * [https://github.com/kuongee/my-js/blob/kuongee/Frontend/JavaScript/varConstLet.md](https://github.com/kuongee/my-js/blob/kuongee/Frontend/JavaScript/varConstLet.md)
* 클로저가 뭐고 언제 쓰이는지
  * [https://github.com/kuongee/my-js/blob/kuongee/Frontend/closure.md](https://github.com/kuongee/my-js/blob/kuongee/Frontend/closure.md)

## Vue

* MVVM
  * Model -&gt; data
  * View -&gt; HTML
  * ViewModel -&gt; Vue 객체
  * 동작
    * MVVM 패턴의 동작 순서는 아래와 같습니다.
      1. 사용자의 Action들은 View를 통해 들어오게 됩니다.
      2. View에 Action이 들어오면, Command 패턴으로 View Model에 Action을 전달합니다.
      3. View Model은 Model에게 데이터를 요청합니다.
      4. Model은 View Model에게 요청받은 데이터를 응답합니다.
      5. View Model은 응답 받은 데이터를 가공하여 저장합니다.
      6. View는 View Model과 Data Binding하여 화면을 나타냅니다.
  * DOM이 변경됐을 때, 뷰모델의 DOM Listeners를 거쳐서 모델로 신호가 간다.
  * 모델에서 변경된 데이터를 뷰모델을 거쳐서 뷰로 보냈을 때, 화면이 reactive하게 반응이 일어난다.
* 라이프사이클
  * [https://mygumi.tistory.com/201?category=697395](https://mygumi.tistory.com/201?category=697395)
  * Lifecycle hooks allow you to know when your component is created, added to the DOM, updated, or destroyed.
  * [https://alligator.io/vuejs/component-lifecycle/](https://alligator.io/vuejs/component-lifecycle/)
* 옵션
  * data, props, computed, methods, watch, emits
  * **computed** 
    * 캐싱 된다는 것이 핵심, 반응형 종속성이 변경될 때에만 다시 계산
  * methods
    * 화살표 함수 사용하면 안됨, 그럼 상위 컨텍스트에 바인딩 되니까
  * **data** 
    * **Restriction:** Only accepts `Function` when used in a component definition.
    * 동일한 컴포넌트가 여러 번 사용되더라도 동일한 객체를 가리키는 것이 아니라 함수가 호출될 때마다 만들어진 객체가 리턴되기 되어 서로 다른 객체를 참조할 수 있기 때문이라고 합니다.
    * 하지만 컴포넌트에서의 Data 선언은 다르다. 각각의 다른 컴포넌트마다 각자의 데이터를 관리해야 하기 때문이다. 컴포넌트마다 Data를 오브젝트로 생성하여 여러 번 사용하더라도 결국엔 JS가 작동하는 방식으로 인해 구성 요소의 모든 단일 인스턴스가이 속성을 공유하여 Data 값을 참조하기 때문에 Data 침범이 일어날 수 있다.

      이러한 이유 때문에 컴포넌트에서는 객체 리터럴로 선언하는 것이 아니라 함수형으로 return 값을 통해 리터럴을 반환한다. return을 이용하면 각 컴포넌트마다 데이터를 분리하여 관리할 수 있게 된다.

    * [https://hj-tilblog.tistory.com/78?category=914136](https://hj-tilblog.tistory.com/78?category=914136)
    * [https://vuejs.org/v2/guide/reactivity.html](https://vuejs.org/v2/guide/reactivity.html)
* vue 지시자 몇가지 이야기해봐라
  * v-if / v-else
  * v-show
  * v-for
  * 
* v-if, v-for 같이 사용하면 안되는 이유는?
  *  2.x에서는 동일한 엘리먼트에 `v-if`와 `v-for`를 함께 사용할 때, `v-for`가 더 높은 우선순위를 갖습니다.
    * This is very bad practice. Don't do it again. The problem with this is that VueJS prioritizes the v-for directive over the v-if directive. So under the hood, it loops through every element and THEN checks the v-if conditional.
    * 그래서 가능하면 computed로 array filtering 하거나 v-for를 밖으로 빼거나
  * 3.x에서는 `v-if`가 항상 `v-for` 보다 더 높은 우선순위를 갖습니다.
  * [https://v3.ko.vuejs.org/guide/migration/v-if-v-for.html\#%E1%84%80%E1%85%A2%E1%84%8B%E1%85%AD](https://v3.ko.vuejs.org/guide/migration/v-if-v-for.html#%E1%84%80%E1%85%A2%E1%84%8B%E1%85%AD)

## React vs. Vue

* virtual DOM
  * [https://mygumi.tistory.com/190](https://mygumi.tistory.com/190)
* React/Vue 비교 해봐라
  * Vue 2.x 버전에서는 하나의 vue 파일에 template, script, style이 다 나눠져있음 React는 하나로 합쳐져 있는 거 같음
  * 컴포넌트 내 data 업데이트가 좀 다른데  vue는 data로 선언된 데이터들에 직접 값을 갱신하면 되고, react는 setState로 갱신해야 한다.
  * [https://erwinousy.medium.com/난-react와-vue에서-완전히-같은-앱을-만들었다-이것은-그-차이점이다-5cffcbfe287f](https://erwinousy.medium.com/%EB%82%9C-react%EC%99%80-vue%EC%97%90%EC%84%9C-%EC%99%84%EC%A0%84%ED%9E%88-%EA%B0%99%EC%9D%80-%EC%95%B1%EC%9D%84-%EB%A7%8C%EB%93%A4%EC%97%88%EB%8B%A4-%EC%9D%B4%EA%B2%83%EC%9D%80-%EA%B7%B8-%EC%B0%A8%EC%9D%B4%EC%A0%90%EC%9D%B4%EB%8B%A4-5cffcbfe287f)
* React/Vue lifecycle 어떻게 다른지
  * [https://frontendsociety.com/transitioning-from-react-to-vue-c9aa943bd0da](https://frontendsociety.com/transitioning-from-react-to-vue-c9aa943bd0da)
    * `constructor` → [`created`](https://vuejs.org/v2/api/#created)
    * `componentWillMount` → [`beforeMount`](https://vuejs.org/v2/api/#beforeMount)
    * `componentDidMount` → [`mounted`](https://vuejs.org/v2/api/#mounted)
    * `componentWillUnmount` → [`beforeDestroy`](https://vuejs.org/v2/api/#beforeDestroy)
    * `componentDidCatch` → _n/a_
    * `shouldComponentUpdate` → _n/a_
    * `setState` → _n/a — just set property directly \(see “_Managing Component State and Data_” below\)_
* React의 componentDidMount가 Vue에서는 어떤 부분일까?
  * mounted
  * 마운트 된 다음에 호출되는 라이프사이클

## 아직 답 안 달은 질문

* react를 깊이 공부한 적이 있는지
* OOP 개념 설명
* call, apply, bind
* 좋은 개발자란 무엇일까?
* 좋은 프로그래머?에 대해 책을 읽어본 적이 있는지
* 해시테이블이 뭐야? 내부 구조는 뭐로 되어있을까
* 깃이나 코드리뷰 어떻게 하고 있는지
* Object.assign이 뭔지? 한계
  * 얕은 복사는 참조\(주소\)값의 복사를 나타낸다.
  * assign이나 spread operator는 2차원 객체는 \(객체 안에 객체\) 얕은 복사가 이루어진다.
  * [https://mygumi.tistory.com/322](https://mygumi.tistory.com/322)
  * [https://velog.io/@recordboy/](https://velog.io/@recordboy/JavaScript-%EC%96%95%EC%9D%80-%EB%B3%B5%EC%82%ACShallow-Copy%EC%99%80-%EA%B9%8A%EC%9D%80-%EB%B3%B5%EC%82%ACDeep-Copy)JavaScript-얕은-복사Shallow-Copy와-깊은-복사Deep-Copy
* REST API가 뭔지, 행동 4개
* function이랑 화살표 함수 차이
* function / class 차이
  * [https://davidtang.io/javascript-constructor-functions-and-classes/](https://davidtang.io/javascript-constructor-functions-and-classes/)
  * [https://github.com/kuongee/my-js/blob/kuongee/Frontend/object.md](https://github.com/kuongee/my-js/blob/kuongee/Frontend/object.md)
  * [https://uiyoji-journal.tistory.com/101](https://uiyoji-journal.tistory.com/101)
* babel을 하나의 단어로 표현하면?
* this에 대해서도 이야기 한 거 같음
* Promise가 뭔지 어떤 문제 때문에 async/await가 나왔는지

  \(내가 promise의 한계로 에러처리 안된다고 했더니 async/await에서는 어떻게 에러처리 했냐고 물어보심\)

