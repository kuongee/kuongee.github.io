# \[React\] Life cycle

[http://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/](http://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/)  
****

**마운트**

아래 메서드들은 컴포넌트의 인스턴스가 생성되어 DOM 상에 삽입될 때에 순서대로 호출

* constructor\(\)
* static getDerivedStateFromProps\(\)
* render\(\)
* componentDidMount\(\)

**업데이트**

props 또는 state가 변경되면 갱신이 발생 / 아래 메서드들은 컴포넌트가 다시 렌더링될 때 순서대로 호출

* static getDerivedStateFromProps\(\)
* shouldComponentUpdate\(\)
* render\(\)
* getSnapshotBeforeUpdate\(\)
* componentDidUpdate\(\)

마운트 해제

아래 메서드는 컴포넌트가 DOM 상에서 제거될 때에 호출

* componentWillUnmount\(\)

**getDerivedStateFromProps**

render 메서드 호출 직전에 호출

시간이 흐름에 따라 변하는 props에 state가 의존하는 예를 위해 존재

props를 받아 state를 업데이트 하고 싶을 때, this를 참조할 수 없음

<table>
  <thead>
    <tr>
      <th style="text-align:left">
        <p><code>getDerivedStateFromProps</code> exists for only one purpose. It enables
          a component to update its internal state as the result of <b>changes in props</b>.</p>
        <p>Our previous blog post provided some examples, like <a href="https://ko.reactjs.org/blog/2018/03/27/update-on-async-rendering.html#updating-state-based-on-props">recording the current scroll direction based on a changing offset prop</a> or
          <a
          href="https://ko.reactjs.org/blog/2018/03/27/update-on-async-rendering.html#fetching-external-data-when-props-change">loading external data specified by a source prop</a>.</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

**componentDidUpdate**

[**https://ko.reactjs.org/docs/react-component.html\#componentdidupdate**](https://ko.reactjs.org/docs/react-component.html#componentdidupdate)  
****

<table>
  <thead>
    <tr>
      <th style="text-align:left">
        <p>&#xCEF4;&#xD3EC;&#xB10C;&#xD2B8;&#xAC00; &#xAC31;&#xC2E0;&#xB418;&#xC5C8;&#xC744;
          &#xB54C; DOM&#xC744; &#xC870;&#xC791;&#xD558;&#xAE30; &#xC704;&#xD558;&#xC5EC;
          &#xC774; &#xBA54;&#xC11C;&#xB4DC;&#xB97C; &#xD65C;&#xC6A9;&#xD558;&#xBA74;
          &#xC88B;&#xC2B5;&#xB2C8;&#xB2E4;. &#xB610;&#xD55C;, &#xC774;&#xC804;&#xACFC;
          &#xD604;&#xC7AC;&#xC758; props&#xB97C; &#xBE44;&#xAD50;&#xD558;&#xC5EC;
          &#xB124;&#xD2B8;&#xC6CC;&#xD06C; &#xC694;&#xCCAD;&#xC744; &#xBCF4;&#xB0B4;&#xB294;
          &#xC791;&#xC5C5;&#xB3C4; &#xC774; &#xBA54;&#xC11C;&#xB4DC;&#xC5D0;&#xC11C;
          &#xC774;&#xB8E8;&#xC5B4;&#xC9C0;&#xBA74; &#xB429;&#xB2C8;&#xB2E4; (&#xAC00;&#xB839;,
          props&#xAC00; &#xBCC0;&#xD558;&#xC9C0; &#xC54A;&#xC558;&#xB2E4;&#xBA74;
          &#xB124;&#xD2B8;&#xC6CC;&#xD06C; &#xC694;&#xCCAD;&#xC744; &#xBCF4;&#xB0BC;
          &#xD544;&#xC694;&#xAC00; &#xC5C6;&#xC2B5;&#xB2C8;&#xB2E4;).</p>
        <p><code>componentDidUpdate()</code>&#xC5D0;&#xC11C; <b><code>setState()</code>&#xB97C; &#xC989;&#xC2DC; &#xD638;&#xCD9C;&#xD560; &#xC218;&#xB3C4; &#xC788;&#xC9C0;&#xB9CC;,</b> &#xC704;&#xC758;
          &#xC608;&#xC2DC;&#xCC98;&#xB7FC; <b>&#xC870;&#xAC74;&#xBB38;&#xC73C;&#xB85C; &#xAC10;&#xC2F8;&#xC9C0;</b> &#xC54A;&#xC73C;&#xBA74;
          &#xBB34;&#xD55C; &#xBC18;&#xBCF5;&#xC774; &#xBC1C;&#xC0DD;&#xD560; &#xC218;
          &#xC788;&#xB2E4;&#xB294; &#xC810;&#xC5D0; &#xC8FC;&#xC758;&#xD558;&#xC138;&#xC694;.
          &#xB610;&#xD55C; &#xCD94;&#xAC00;&#xC801;&#xC778; &#xB80C;&#xB354;&#xB9C1;&#xC744;
          &#xC720;&#xBC1C;&#xD558;&#xC5EC;, &#xBE44;&#xB85D; &#xC0AC;&#xC6A9;&#xC790;&#xB294;
          &#xB208;&#xCE58;&#xCC44;&#xC9C0; &#xBABB;&#xD560;&#xC9C0;&#xB77C;&#xB3C4;
          &#xCEF4;&#xD3EC;&#xB10C;&#xD2B8; &#xC131;&#xB2A5;&#xC5D0; &#xC601;&#xD5A5;&#xC744;
          &#xBBF8;&#xCE60; &#xC218; &#xC788;&#xC2B5;&#xB2C8;&#xB2E4;. &#xC0C1;&#xC704;&#xC5D0;&#xC11C;
          &#xB0B4;&#xB824;&#xC628; prop&#xC744; &#xADF8;&#xB300;&#xB85C; state&#xC5D0;
          &#xC800;&#xC7A5;&#xD558;&#xB294; &#xAC83;&#xC740; &#xC88B;&#xC9C0; &#xC54A;&#xC73C;&#xBA70;,
          &#xADF8; &#xB300;&#xC2E0; prop&#xC744; &#xC9C1;&#xC811; &#xC0AC;&#xC6A9;&#xD558;&#xB294;
          &#xAC83;&#xC774; &#xC88B;&#xC2B5;&#xB2C8;&#xB2E4;. &#xC774;&#xC640; &#xAD00;&#xB828;&#xB41C;
          &#xC790;&#xC138;&#xD55C; &#xC815;&#xBCF4;&#xB294; <a href="https://ko.reactjs.org/blog/2018/06/07/you-probably-dont-need-derived-state.html">props&#xB97C; state&#xC5D0; &#xBCF5;&#xC0AC;&#xD558;&#xB294; &#xAC83;&#xC774; &#xBC84;&#xADF8;&#xB97C; &#xC720;&#xBC1C;&#xD558;&#xB294; &#xC774;&#xC720;</a>&#xC5D0;&#xC11C;
          &#xD655;&#xC778;&#xD560; &#xC218; &#xC788;&#xC2B5;&#xB2C8;&#xB2E4;.</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

#### Side effects on props change

Like `componentWillUpdate`, `componentWillReceiveProps` might get called multiple times for a single update. For this reason it is important to avoid putting side effects in this method. Instead, `componentDidUpdate` should be used since it is guaranteed to be invoked only once per update: \(componentDidUpdate는 딱 한번 업데이트 될거라고 보장될 때 불리니까\)

그럼 데이터 fetch는 언제 하냐

The recommended upgrade path for this component is to move data updates into `componentDidUpdate`. You can also use the new `getDerivedStateFromProps` lifecycle to clear stale data before rendering the new props:

또다른 blog→

b. Never use it for API calls, the asynchronous data fetching requests may initiate multiple times and multiple renders may hinder the user experience, use `componentDidMount` instead.  
[https://medium.com/@saharshgoyal/react-16-new-life-cycle-methods-inside-out-fdd269c43ccd](https://medium.com/@saharshgoyal/react-16-new-life-cycle-methods-inside-out-fdd269c43ccd)

### Common Bugs When Using Derived State

[https://ko.reactjs.org/blog/2018/06/07/you-probably-dont-need-derived-state.html\#common-bugs-when-using-derived-state](https://ko.reactjs.org/blog/2018/06/07/you-probably-dont-need-derived-state.html#common-bugs-when-using-derived-state)

[https://ko.reactjs.org/docs/react-component.html](https://ko.reactjs.org/docs/react-component.html)

상위에서 내려온 prop을 그대로 state에 저장하는 것은 좋지 않으며, 그 대신 prop을 직접 사용하는 것이 좋습니다.

[https://ko.reactjs.org/blog/2018/03/27/update-on-async-rendering.html\#fetching-external-data-when-props-change](https://ko.reactjs.org/blog/2018/03/27/update-on-async-rendering.html#fetching-external-data-when-props-change)

componentDidMount, compondidupdate보다 이전에 호출된 setState는 UI 업데이트 되기 전에  flush

