# \[Vue]로 개발하면서 알게 된 것

### 배열 변경 감지

→ Vue는 감시 중인 배열의 변이 메소드를 래핑하여 뷰 갱신을 트리거한다.\
push, pop, shift, unshift, splice, sort, reverse => 얘네는 원본 배열을 변형\
filter, concat, slice => 항상 새 배열을 반환

arr\[0] = newVal / arr.length = newLength => 이런건 감지 못함

### computed vs. watch

computed는 다른 변화에 대한 응답으로 계산을 업데이트 해야 할 때\
watch는 컴포넌트 외부의 동작/비동기 처리

computed를 써도 되는데 watch를 남용하지 않도록 주의

### i18n lazy loading

vue-i18n 사용

모든 다국어 파일을 한번에 읽어들이는 것은 불필요할 수 있음\
그리고 백엔드로부터 다국어를 로드해야 한다면 lazy loading

[https://kazupon.github.io/vue-i18n/guide/lazy-loading.html](https://kazupon.github.io/vue-i18n/guide/lazy-loading.html)

[https://stackoverflow.com/questions/55722512/internationalization-in-vue-js-using-vue-i18n-getting-json-object-from-api-serve](https://stackoverflow.com/questions/55722512/internationalization-in-vue-js-using-vue-i18n-getting-json-object-from-api-serve)

### Vuex store

상태 관리

GOV에서는 로딩 상태, 글로벌 필터 상태, 로그인 상태 등을 관리하고 있음\


### Vue Router (+SPA 라우팅)

* [https://router.vuejs.org/kr/guide/essentials/nested-routes.html](https://router.vuejs.org/kr/guide/essentials/nested-routes.html)
* [https://jeonghwan-kim.github.io/2018/04/07/vue-router.html](https://jeonghwan-kim.github.io/2018/04/07/vue-router.html)

#### SPA에서 라우팅

초기 앱에서 로드할 때 모든 웹 사이트 컨텐츠를 로드, URL 경로에 따라 페이지를 동적으로 표현 → 라우팅으로\
이미 다 올라와있기 때문에 필요할 때마다 문서를 요청하는 방식보다 빠름

#### SPA

[https://poiemaweb.com/js-spa](https://poiemaweb.com/js-spa)

#### SPA에 왜 # hashed url을 주로 사용할까?

[https://blog.bitsrc.io/using-hashed-vs-nonhashed-url-paths-in-single-page-apps-a66234cefc96](https://blog.bitsrc.io/using-hashed-vs-nonhashed-url-paths-in-single-page-apps-a66234cefc96)\


