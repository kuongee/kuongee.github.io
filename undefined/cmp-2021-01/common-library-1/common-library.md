# Common Library 분리



cmp-portal-library

* Vue plugin 형태로 제공 → Vue.use로 사용
* vueRouter, commonAxios, eventBus, (initLibrary) 외부에서도 사용할 수 있도록 제공\
  initLibrary는 라이브러리 외부에서 전달받은 정보로 비동기적으로 설정하는 구조 (현재는 구조만 잡혀있음)

설치

1. cmp\_portal\_library git 다운로드\
   라이브러리를 사용할 다른 코드의 디렉토리와 동일한 곳에 위치시킴
2. npm install
3. build
   * (프로덕션) npm run build
   * (개발) npm run build:dev\

4. Container 또는 Micro FE에 라이브러리 추가하기

```
npm install --save ../cmp-portal-library
```

```
// 예시
import portalLib, { vueRouter }  from "cmp-portal-library";
import cmpComponentsfrom 'cmp-portal-component';
import axiosInterceptors from './config/axios/axiosInterceptors';

Vue.use(portalLib, {/* config */});
axiosInterceptors(Vue, Vue.prototype.$http); // axios interceptors는 필요하면 외부에서 설정

const router = new vueRouter({ routes });
```
