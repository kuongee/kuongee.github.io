# Container 내에 AUI 올리기

### MainView가 올라오기 전 navigate가 호출되었을 때 <a id="id-[CMP]Container&#xB0B4;&#xC5D0;AUI&#xC62C;&#xB9AC;&#xAE30;-MainView&#xAC00;&#xC62C;&#xB77C;&#xC624;&#xAE30;&#xC804;navigate&#xAC00;&#xD638;&#xCD9C;&#xB418;&#xC5C8;&#xC744;&#xB54C;"></a>

컨테이너 Main 화면에서 새로고침을 한 후 바로 'Go to AUI Sample'을 누르면 AUI의 MainView, MiddleLayoutView가 모두 올라오기 전에 navigate를 호출한다. 이 경우 navigate 함수에서 MiddleLayoutView로 publish 할 때 이걸 받지 못하게 된다.

MainView와 MiddleLayoutView가 정상적으로 로드될 것이라고 가정

MiddleLayoutView에 id를 추가함

```markup
<div id="test-middle" class="Container-inner" data-camellia-view="common.main.middle.MiddleLayoutView"></div>
```

AuiConnector.js에 정의되어있는 navigate 함수에서 위 id의 html 원소가 있는지 확인

있으면 그대로 navigate 호출

없을 때 다음과 같은 2가지 방법으로 해봄

1. setTimeout으로 1초 정도 후에 navigate 호출하도록 함
2. 여기 참고해봄[→ https://stackoverflow.com/questions/16149431/make-function-wait-until-element-exists/47776379](https://stackoverflow.com/questions/16149431/make-function-wait-until-element-exists/47776379)

```javascript
function rafAsync() {
      return new Promise(resolve => {
          requestAnimationFrame(resolve); //faster than set time out
      });
    }
 
 
function checkElement(selector) {
  if (document.querySelector(selector) === null) {
      return rafAsync().then(() => checkElement(selector));
  } else {
      return Promise.resolve(true);
  }
}
 
if(!document.getElementById('test-middle')) {
  console.log('test middle');
  checkElement('#test-middle') //use whichever selector you want
  .then((element) => {
      console.info('test-middle ', element);
      AP.navigationService.navigate({ route: url, isReplace: true });
      //Do whatever you want now the element is there
});
```

※ NavigationService.js &gt; navigate 함수 마지막 줄에 checkSession 함수 내\(아래 코드\)에서 에러가 발생하고 catch에서 처리하고 있기 때문에 에러가 표시되지 않음

```javascript
// 395, 396번째 줄
AP.run(this.$renderMainPage.bind(this));
this.$selectors.loginFail.hide();
 
 
// 이 부분을 다음과 같이 수정하면 해결된다.
// rootView를 직접 가져온다.
var rootView = AP.util.view.getAPRootViewInstance();
rootView.$renderMainPage();
// *** 논의 필요: renderMainPage를 하면 mainView 원소가 중복되어 추가된다.
```

### New CMP 실행되면서 AP 객체 못 찾는 문제 <a id="id-[CMP]Container&#xB0B4;&#xC5D0;AUI&#xC62C;&#xB9AC;&#xAE30;-NewCMP&#xC2E4;&#xD589;&#xB418;&#xBA74;&#xC11C;AP&#xAC1D;&#xCCB4;&#xBABB;&#xCC3E;&#xB294;&#xBB38;&#xC81C;"></a>

위의 requestAnimationFrame을 여기서도 활용해보기

AUI 화면에서 새로고침 했을 때

* AP 로드 되었는지 확인 → AP.navigationService 로드 되었는지 확인 → mainView 로드 되었는지 확인
  * 이렇게 하면 3번의 확인을 거쳐야 하는데 문제가 없을지 논의가 필요 \(코드가 복잡해짐\)

AP가 로드되었는지는 applicationActive 이벤트가 호출로 판단 \(정확히 applicationActive가 언제 호출되는지에 대한 정보는 부족\)

* APRootView에서 render가 끝나면 applicationActive 이벤트가 호출 →  AP 객체가 모두 로드되었다고 가정할 수 있어보임

```javascript
// AuiConnector.js
// initAui 함수 내부
A.application.on('applicationActive', function() {
 
      store.commit(MUTATION_TYPE.APPLICATION_ACTIVE, { active: true });
      store.dispatch('loadMiddleLayoutView');
 
      this.subscribe('app.login.retry', (message) => {
        // Login 수행
        Vue.prototype.$cmpLogin.login();
      });
    }.bind(this));
 
// AUI 시작
A.application.run();
```

store를 사용함

AP 객체와 MainView &gt; MiddleLayoutView가 로드되었는지를 판단하여 navigate에서 각 상태를 불러와 확인

#### ※ 결론 <a id="id-[CMP]Container&#xB0B4;&#xC5D0;AUI&#xC62C;&#xB9AC;&#xAE30;-&#x203B;&#xACB0;&#xB860;"></a>

MiddleLayoutView에서 View가 READY 되면 발생하는 이벤트를 사용하기로 함

auiConnector에서 subscribe 시켜놓고 READY 이벤트에서 publish하면 store에 flag 값을 true로 표시

만약 view가 로드 되기 전 navigate 함수가 불렸다면 flag 값이 true가 될 때까지 기다렸다가 실행되도록

