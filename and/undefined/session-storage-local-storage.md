# Session Storage, Local Storage, 쿠키

HTML5의 WebStorage API 중 하나인 Local storage, session storage

만약 한 도메인을 위한 세션스토리지를 조작하고 싶다면, Window.sessionStorage 메서드를 사용하면 됩니다. 마찬가지로, 로컬스토리지의 경우에는 Window.localStorage를 사용합니다.

[https://developer.mozilla.org/ko/docs/Web/API/Storage](https://developer.mozilla.org/ko/docs/Web/API/Storage)

#### Session Storage

[https://developer.mozilla.org/ko/docs/Web/API/Window/sessionStorage](https://developer.mozilla.org/ko/docs/Web/API/Window/sessionStorage)

Window.sessionStorage

sessionStorage 속성이 원래 정의되어 있어서 session Storage 객체에 접근할 수 있게 해주나봄

sessionStorage에 저장된 데이터는 페이지 세션이 종료되면 바로 지워진다.

윈도우 창, 탭 별로 유지\(공유 안 됨\)

**세션**

앞서 살펴본 쿠키는 클라이언트 측의 컴퓨터에 모든 데이터를 저장합니다.

하지만 세션은 서비스가 돌아가는 서버 측에 데이터를 저장하고, 세션의 키값만을 클라이언트 측에 남겨둡니다.

브라우저는 필요할 때마다 이 키값을 이용하여 서버에 저장된 데이터를 사용하게 됩니다.

[http://tcpschool.com/php/php\_cookieSession\_session](http://tcpschool.com/php/php_cookieSession_session)

#### Local Storage

로컬 스토리지의 내용이 변경되었을 때 'storage' 이벤트가 발생

사용자가 직접 데이터를 삭제하기 전까지는 영구적으로 보관

#### cookie

쿠키 vs. localstorage

서버측과 클라이언트 측 양쪽에서 쿠키 데이터를 사용하는 api가 존재

localstorage는 로컬 환경에서만 컨트롤

[https://medium.com/datadriveninvestor/cookies-vs-local-storage-2f3732c7d977](https://medium.com/datadriveninvestor/cookies-vs-local-storage-2f3732c7d977)

### **그럼 세션 스토리지를 어떻게 공유할 것이냐?**

세션 스토리지는 창, 탭 별로 되어있음

[https://medium.com/@marciomariani/sharing-sessionstorage-between-tabs-5b6f42c6348c](https://medium.com/@marciomariani/sharing-sessionstorage-between-tabs-5b6f42c6348c)

