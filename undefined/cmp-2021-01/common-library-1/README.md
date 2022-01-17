# Common Library 만들기

AS-IS

Common Component Library에 공통 라이브러리들과 공통 컴포넌트들이 합쳐져 있다.

TO-BE

Common Library (Router, Store, i18n, Axios 등등)와 Component Library (Component, Style) 을 완전 분리



### 노트

#### node.js와 npm

node.js는 브라우저 외부 환경에서 자바스크립트 애플리케이션 개발에 사용된다.

npm은 자바스크립트 패키지 매니저. Node.js에서 사용할 수 있는 모듈들을 패키지화하여 모아둔 저장소 역할과 패키지 설치 및 관리를 위한 CLI를 제공한다.

npm은 package.json 파일을 통해서 프로젝트 정보와 패키지의 의존성(dependency)를 관리한다.

* name과 version은 생략할 수 없다.
* dependencies\
  프로젝트가 의존하는 패키지들의 이름과 버전을 명시한다.
* devDependencies\
  개발 시에만 사용하는 개발용 의존 패키지를 명시한다. (예로 트랜스파일러는 개발 단계에서만 필요하고 배포할 필요는 없으니까 여기에 넣는다.)
* main\
  프로그램의 시작점(entry point)를 지정한다.\
  예를 들어 package.json에 다음과 같이 정의되어있다고 가정할 때

```
{
    "name": "zig-zag",
	"main": "lib/entry.js"
	...
}
```

```
require('zig-zag');
```

이렇게 호출하면 lib/entry.js에서 exports 객체로 반환된 값이 불릴 것이다.\
(그런데 모듈/라이브러리로 만들 때는 웹팩의 도움을 받아야 함)

참고

* [https://stackoverflow.com/questions/22512992/how-to-use-the-main-parameter-in-package-json](https://stackoverflow.com/questions/22512992/how-to-use-the-main-parameter-in-package-json)
* 메인에 대한 설명 + 모듈로 만들 때 설명★: [https://ui.toast.com/weekly-pick/ko\_20170818#npm-%EB%93%B1%EB%A1%9D-%EC%9D%B4%EC%8A%88-1%EB%9D%BC%EC%9A%B4%EB%93%9C--%EB%B2%88%EB%93%A4%EB%A7%81](https://ui.toast.com/weekly-pick/ko\_20170818#npm-%EB%93%B1%EB%A1%9D-%EC%9D%B4%EC%8A%88-1%EB%9D%BC%EC%9A%B4%EB%93%9C--%EB%B2%88%EB%93%A4%EB%A7%81)

[https://poiemaweb.com/nodejs-basics](https://poiemaweb.com/nodejs-basics)\
[https://poiemaweb.com/nodejs-npm](https://poiemaweb.com/nodejs-npm)\
[https://nodesource.com/blog/an-absolute-beginners-guide-to-using-npm/](https://nodesource.com/blog/an-absolute-beginners-guide-to-using-npm/)\
[https://nodesource.com/blog/the-basics-of-package-json-in-node-js-and-npm/](https://nodesource.com/blog/the-basics-of-package-json-in-node-js-and-npm/)\
노드란? [https://programmingsummaries.tistory.com/328?category=604662](https://programmingsummaries.tistory.com/328?category=604662)



#### webpack

webpack 어플리케이션을 library 형태로 만들자

[https://trustyoo86.github.io/webpack/2018/01/10/webpack-configuration.html](https://trustyoo86.github.io/webpack/2018/01/10/webpack-configuration.html)

* webpack.config.js

```
const { resolve } = require('path');

module.exports = {
    entry: {
		// entry 키 이름으로 결과물이 나옴
        'cmp-portal-library': resolve(__dirname, 'src/index.js'),
    },
    output: {
        library: 'cmp-portal-library',
        libraryTarget: 'umd',
        path: resolve(__dirname, 'dist'),
        filename: '[name].js',
    }
}
```

* webpack 설치

```
npm i -D webpack webpack-cli
```

[https://meetup.toast.com/posts/153](https://meetup.toast.com/posts/153)

[https://ui.toast.com/weekly-pick/ko\_20170818#npm-%EB%93%B1%EB%A1%9D-%EC%9D%B4%EC%8A%88-1%EB%9D%BC%EC%9A%B4%EB%93%9C--%EB%B2%88%EB%93%A4%EB%A7%81](https://ui.toast.com/weekly-pick/ko\_20170818#npm-%EB%93%B1%EB%A1%9D-%EC%9D%B4%EC%8A%88-1%EB%9D%BC%EC%9A%B4%EB%93%9C--%EB%B2%88%EB%93%A4%EB%A7%81)

[https://www.zerocho.com/category/Webpack/post/58aa916d745ca90018e5301d](https://www.zerocho.com/category/Webpack/post/58aa916d745ca90018e5301d)

[https://ui.toast.com/weekly-pick/ko\_20170818](https://ui.toast.com/weekly-pick/ko\_20170818)

웹팩5로 청크 관리 및 코드 스플리팅 하기

[https://www.zerocho.com/category/Webpack/post/58ad4c9d1136440018ba44e7](https://www.zerocho.com/category/Webpack/post/58ad4c9d1136440018ba44e7)

코드 스플리팅 하는 이유

라이브러리 파일들은 보통 chunk-vendors.js 파일에 번들링되지만 내가 만든 라이브러리는 별도의 파일로 분리하여 빌드한다.

왜냐하면 컨테이너랑 micro랑 중복으로 들어갈 필요가 없기 때문에

#### 프로젝트 초기 세팅

gerrit의 cmp\_user\_portal\_component repository의 directory 이름을 **cmp\_portal\_library**로 사용한다.

```
git clone ssh://jeesoo.min@gerrit.score:29418/cmp_user_portal_component cmp_portal_library && scp -p -P 29418 jeesoo.min@gerrit.score:hooks/commit-msg cmp_user_portal_component/.git/hooks/
```

cmp\_portal\_library에 orphan branch로 common-library를 만든다.

npm init

프로젝트를 초기화 한다.

#### 프로젝트 pull 받을 때

cmp\_user\_portal\_component → directory 이름을 cmp\_portal\_library로 설정하고 branch는 common-library로 변경

기존 component 코드

main.js

vueCookie, vueI18n, vueRouter, axios 다 지움

frontend (container) 코드 → branch를 common-library로 변경

(main.js → portalLib으로 변경)



```
import Vue from 'vue'
import store from './store';
import CommonLib from 'lego-library';
import cmpLogin from 'cmp-portal-login';
// import CommonLib, { initLegoBuilder, store, Router } from 'lego-library';
import App from './App.vue'
import routes from './routes';
import AuiConnector from './AuiConnector';
import portalLib, { vueRouter }  from "cmp-portal-library";
import axiosInterceptors from './config/axios/axiosInterceptors';


Vue.use(portalLib, {/* config */});
axiosInterceptors(Vue, Vue.prototype.$http); // axios interceptor 설정하는 거는 공통 라이브러리에서 말고 외부에서 하도록
```
