# \[Javascript\] Module

### JavaScript Module <a id="Module&#xAD00;&#xB828;-JavaScriptModule"></a>

* 모듈이란?
  * 구현 세부 사항을 캡슐화하고 공개 API를 노출해 다른 코드에서 쉽게 로드하고 사용할 수 있는 재사용 가능한 코드 조각
  * 다른 언어들과 달리 JavaScript는 외부 스크립트 파일은 가져올 수 있지만 파일마다 독립적인 파일 scope를 가지고 있지 않아서 하나의 전역 객체로 취급되어 전역변수가 중복되는 문제 등이 생길 수 있음
  * 모듈화를 구현할 수 없는 경우, 브라우저에서 모듈을 사용할 수 있도록 하는 모듈 시스템\(모듈 로더 라이브러리\) 사용하기도 함
* 모듈 포맷
  * 모듈을 정의하기 위한 공식적인 문법이 없었을 때 모듈을 정의하기 위한 포맷
  * CommonJS
    * require와 module.exports를 사용해서 의존성과 모듈을 정의
    * node.js 에서 사용하는 방식
  * AMD
    * define
  * UMD
* ES6부터는 JavaScript에서도 내장된 모듈 포맷 사용 가능
  * 브라우저에서는 지원되고 있지 않아서 Babel과 같은 변환기를 사용해서 다른 모듈 포맷으로 코드 변환이 필요
    * \(최근 브라우저 자체에서도 지원하고 있는 거 같음\)
  * import, export를 사용할 수 있는 모듈시스템을 사용할 수 있음
    * import 키워드로는 외부 모듈을 가져올 수 있음
    * export 키워드로는 모듈을 내보냄
* 모듈 로더
  * 주요 모듈 포맷으로 작성된 모듈을 해석하고 로드
  * 런타임에 실행
  * RequireJS, SystemJS
* **모듈 번들러**
  * 모듈 로더를 대체하고 모든 코드의 번들을 생성
    * 분리되어 있던 모듈과 자원들이 하나의 번들로 만들어짐
  * 빌드타임에 실행
  * 브라우저에서 번들파일을 로드
  * Webpack
  * Browserify
  * parceljs
* **Reference**
  * 모듈 소개, 모듈포맷, 모듈로더, 모듈 번들러 설명
    * [https://jvandemo.com/a-10-minute-primer-to-javascript-modules-module-formats-module-loaders-and-module-bundlers/?utm\_source=javascriptweekly&utm\_medium=email\#](https://jvandemo.com/a-10-minute-primer-to-javascript-modules-module-formats-module-loaders-and-module-bundlers/?utm_source=javascriptweekly&utm_medium=email)
    * [https://github.com/codepink/codepink.github.com/wiki/자바스크립트-모듈,-모듈-포맷,-모듈-로더와-모듈-번들러에-대한-10분-입문서](https://github.com/codepink/codepink.github.com/wiki/자바스크립트-모듈,-모듈-포맷,-모듈-로더와-모듈-번들러에-대한-10분-입문서)
  * 자바스크립트에서 모듈을 사용할 수 없었던 이유
    * [https://poiemaweb.com/es6-module](https://poiemaweb.com/es6-module)
    * [https://jeong-pro.tistory.com/122](https://jeong-pro.tistory.com/122)
  * CommonJS, AMD 설명
    * [https://programmingsummaries.tistory.com/321](https://programmingsummaries.tistory.com/321)
  * [https://github.com/nhnent/fe.javascript/wiki/%23164:-웹에서-자바스크립트-모듈-사용하기](https://github.com/nhnent/fe.javascript/wiki/%23164:-웹에서-자바스크립트-모듈-사용하기)

