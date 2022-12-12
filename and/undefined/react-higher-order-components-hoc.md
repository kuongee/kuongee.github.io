# \[React] Higher-Order Components (HOC)



리액트 컴포넌트의 특징으로 나타난 패턴 (리액트에서 제공하는 API 아님)

* 반복되는 코드를 줄이자 → 컴포넌트 로직의 재사용
* 하나의 컴포넌트는 props를 받아서 UI로 변환하지만, **하나의 컴포넌트를 인자로 받아서 새로운 컴포넌트를 반환하는 함수** (리액트의 컴포넌트는 기본적으로 함수)

| <p>Concretely, <strong>a higher-order component is a function that takes a component and returns a new component.</strong></p><p>출처: <a href="https://ko.reactjs.org/docs/higher-order-components.html">https://ko.reactjs.org/docs/higher-order-components.html</a></p> |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |

예시) 노란색 별을 넣으면 노란 별을 포함하는 새로운 컴포넌트가 그려지고, 파란색별을 넣으면 파란 별을 포함하는 새로운 컴포넌트가 반환될 것이다.

![](<../../.gitbook/assets/image (25).png>)

* 왜 HOC가 유용한지?
  *   Cross-Cutting Concerns를 위해서 써라

      * Cross-Cutting Concerns: [https://stackoverflow.com/questions/23700540/cross-cutting-concern-example](https://stackoverflow.com/questions/23700540/cross-cutting-concern-example)



**Reference**

* [https://reactjs.org/docs/higher-order-components.html](https://reactjs.org/docs/higher-order-components.html)
* [https://www.vobour.com/%EB%A6%AC%EC%95%A1%ED%8A%B8-react-%EC%9D%B4%ED%95%B4-4-higher-order-component](https://www.vobour.com/%EB%A6%AC%EC%95%A1%ED%8A%B8-react-%EC%9D%B4%ED%95%B4-4-higher-order-component)
* [https://velopert.com/3537](https://velopert.com/3537)



HoC의 한계

Wrapper 지옥

[https://velog.io/@vies00/React-Hooks](https://velog.io/@vies00/React-Hooks)

↓

Hooks로 벗어날 수 있다. [Hooks](http://confluence.score/display/\~jeesoo.min/Hooks)

16.8 버전 도입

Hooks: React를 class 선언 없이 함수형으로 사용할 수 있게 하는 기능(render 에만 들어가는 기능 개발)

[https://velog.io/@velopert/react-hooks](https://velog.io/@velopert/react-hooks)

[https://mk.kakaocdn.net/dn/if-kakao/conf2019/%EB%B0%9C%ED%91%9C%EC%9E%90%EB%A3%8C\_2019/T04-S01.pdf](https://mk.kakaocdn.net/dn/if-kakao/conf2019/%EB%B0%9C%ED%91%9C%EC%9E%90%EB%A3%8C\_2019/T04-S01.pdf)
