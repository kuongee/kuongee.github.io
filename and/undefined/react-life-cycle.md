# \[React] Life cycle

[http://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/](http://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/)****\
****

**마운트**

아래 메서드들은 컴포넌트의 인스턴스가 생성되어 DOM 상에 삽입될 때에 순서대로 호출

* constructor()
* static getDerivedStateFromProps()
* render()
* componentDidMount()

**업데이트**

props 또는 state가 변경되면 갱신이 발생 / 아래 메서드들은 컴포넌트가 다시 렌더링될 때 순서대로 호출

* static getDerivedStateFromProps()
* shouldComponentUpdate()
* render()
* getSnapshotBeforeUpdate()
* componentDidUpdate()

마운트 해제

아래 메서드는 컴포넌트가 DOM 상에서 제거될 때에 호출

* componentWillUnmount()

**getDerivedStateFromProps**

render 메서드 호출 직전에 호출

시간이 흐름에 따라 변하는 props에 state가 의존하는 예를 위해 존재

props를 받아 state를 업데이트 하고 싶을 때, this를 참조할 수 없음

| <p><code>getDerivedStateFromProps</code> exists for only one purpose. It enables a component to update its internal state as the result of <strong>changes in props</strong>.</p><p>Our previous blog post provided some examples, like <a href="https://ko.reactjs.org/blog/2018/03/27/update-on-async-rendering.html#updating-state-based-on-props">recording the current scroll direction based on a changing offset prop</a> or <a href="https://ko.reactjs.org/blog/2018/03/27/update-on-async-rendering.html#fetching-external-data-when-props-change">loading external data specified by a source prop</a>.</p> |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

**componentDidUpdate**

[**https://ko.reactjs.org/docs/react-component.html#componentdidupdate**](https://ko.reactjs.org/docs/react-component.html#componentdidupdate)****\
****

| <p>컴포넌트가 갱신되었을 때 DOM을 조작하기 위하여 이 메서드를 활용하면 좋습니다. 또한, 이전과 현재의 props를 비교하여 네트워크 요청을 보내는 작업도 이 메서드에서 이루어지면 됩니다 (가령, props가 변하지 않았다면 네트워크 요청을 보낼 필요가 없습니다).</p><p><code>componentDidUpdate()</code>에서 <strong><code>setState()</code>를 즉시 호출할 수도 있지만,</strong> 위의 예시처럼 <strong>조건문으로 감싸지</strong> 않으면 무한 반복이 발생할 수 있다는 점에 주의하세요. 또한 추가적인 렌더링을 유발하여, 비록 사용자는 눈치채지 못할지라도 컴포넌트 성능에 영향을 미칠 수 있습니다. 상위에서 내려온 prop을 그대로 state에 저장하는 것은 좋지 않으며, 그 대신 prop을 직접 사용하는 것이 좋습니다. 이와 관련된 자세한 정보는 <a href="https://ko.reactjs.org/blog/2018/06/07/you-probably-dont-need-derived-state.html">props를 state에 복사하는 것이 버그를 유발하는 이유</a>에서 확인할 수 있습니다.</p> |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

#### Side effects on props change

Like `componentWillUpdate`, `componentWillReceiveProps` might get called multiple times for a single update. For this reason it is important to avoid putting side effects in this method. Instead, `componentDidUpdate` should be used since it is guaranteed to be invoked only once per update: (componentDidUpdate는 딱 한번 업데이트 될거라고 보장될 때 불리니까)

그럼 데이터 fetch는 언제 하냐

The recommended upgrade path for this component is to move data updates into `componentDidUpdate`. You can also use the new `getDerivedStateFromProps` lifecycle to clear stale data before rendering the new props:

또다른 blog→

b. Never use it for API calls, the asynchronous data fetching requests may initiate multiple times and multiple renders may hinder the user experience, use `componentDidMount` instead.\
[https://medium.com/@saharshgoyal/react-16-new-life-cycle-methods-inside-out-fdd269c43ccd](https://medium.com/@saharshgoyal/react-16-new-life-cycle-methods-inside-out-fdd269c43ccd)

### Common Bugs When Using Derived State

[https://ko.reactjs.org/blog/2018/06/07/you-probably-dont-need-derived-state.html#common-bugs-when-using-derived-state](https://ko.reactjs.org/blog/2018/06/07/you-probably-dont-need-derived-state.html#common-bugs-when-using-derived-state)

[https://ko.reactjs.org/docs/react-component.html](https://ko.reactjs.org/docs/react-component.html)

상위에서 내려온 prop을 그대로 state에 저장하는 것은 좋지 않으며, 그 대신 prop을 직접 사용하는 것이 좋습니다.

[https://ko.reactjs.org/blog/2018/03/27/update-on-async-rendering.html#fetching-external-data-when-props-change](https://ko.reactjs.org/blog/2018/03/27/update-on-async-rendering.html#fetching-external-data-when-props-change)

componentDidMount, compondidupdate보다 이전에 호출된 setState는 UI 업데이트 되기 전에  flush
