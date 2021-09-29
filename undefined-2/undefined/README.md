# 면접 질문 답 정리 및 예상 질문 공부

[https://raniee.tistory.com/15](https://raniee.tistory.com/15)

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

## CORS

Cross-Origin Resource Sharing / 교차 출처 리소스 공유

한 출처에서 실행 중인 웹 애플리케이션이 다른 출처의 선택한 자원에 접근할 수 있는 권한을 부여하도록 브라우저에 알려주는 체제

여기서 중요한 사실 한 가지는 이렇게 출처를 비교하는 로직이 서버에 구현된 스펙이 아니라 브라우저에 구현되어 있는 스펙이라는 것이다.

만약 우리가 CORS 정책을 위반하는 리소스 요청을 하더라도 해당 서버가 같은 출처에서 보낸 요청만 받겠다는 로직을 가지고 있는 경우가 아니라면 서버는 정상적으로 응답을 하고, 이후 브라우저가 이 응답을 분석해서 CORS 정책 위반이라고 판단되면 그 응답을 사용하지 않고 그냥 버리는 순서인 것이다.

* Preflight **OPTIONS 메서드**를 통해 다른 도메인의 리소스에 요청이 가능한지 확인 작업 요청 보내기 전에 미리 보내보는 것 RESPONSE로 

![](../../.gitbook/assets/image%20%2832%29.png)

[https://evan-moon.github.io/2020/05/21/about-cors/](https://evan-moon.github.io/2020/05/21/about-cors/)

[https://www.youtube.com/watch?v=-2TgkKYmJt4](https://www.youtube.com/watch?v=-2TgkKYmJt4)

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

