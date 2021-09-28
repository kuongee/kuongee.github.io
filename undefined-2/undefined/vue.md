# Vue

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
  * 비교
    * MVC: Controller에 많은 코드가 몰리게되고, 각 모듈별 의존성이 강해서 변경사항이 발생하면 Model, View, Controller가 모두 변경되어야 합니다.
    * MVP: View와 Model 간의 의존성은 삭제되었으나 View와 Presenter 간의 의존성이 1:1 수준으로 강하게 적용됩니다.
    * MVVM: 데이터 바이딩을 통해 View와 ViewModel은 1:n 관계를 가질 수 있습니다. 이로써 모듈별 의존성이 없어지고 독립적이게 됨으로써 역할별 유닛테스트가 용이하고, 비동기성 코드를 작성할 수 있게됩니다.
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
* Vue에서 화살표함수 쓸 수 없는 거
  * [https://joshua1988.github.io/web-development/translation/essential-es6-features-for-vuejs/](https://joshua1988.github.io/web-development/translation/essential-es6-features-for-vuejs/)
  *  화살표 함수의 중요한 특징은 값을 `this`로 바인딩 하지 않는 것입니다. 대신에, 화살표 함수 안에서 선언한 `this`는 해당 함수가 수행되는 컨텍스트를 가리킵니다.
  * 뷰 인스턴스의 속성들을 정의할 때는 화살표 함수를 사용하면 안 됩니다.
    * 왜냐하면 window를 가리키기 때문
    * methods / computed 에서 

