# Next js, TypeScript

### TypeScript

#### => TS의 primitive type

[https://www.typescriptlang.org/docs/handbook/2/everyday-types.html](https://www.typescriptlang.org/docs/handbook/2/everyday-types.html)

* JavaScript에서 primitive는 object가 아니고 methods를 가지지 않는 데이터를 말한다.\
  그래서 7개의 primitive data type이 있는데: string, number, bigint, boolean, undefined, symbol, null\
  모든 primitive는 immutable
* TS primitives: string, number, boolean (type으로 쓸때는 항상 앞글자 소문자로 써라)

다른 타입들

* Arrays\
  number\[]; 이거랑 \[number] 이거는 다름 뒤에꺼는 Tuples
* any\
  any를 붙이게 되면 이후에는 type checking을 안 하게 됨 (이 말은 내가 TypeScript보다 더 환경을 잘 알고 쓸 수 있다고 가정할 수 있다)
* noImplicitAny\
  type을 명시하지 않으면 TS는 타입을 컨텍스트로 유추해내지 못하기 때문에 컴파일러는 기본적으로 any로 설정한다.\
  이게 싫으면 noImplictAny 컴파일러 flag를 사용해라. (any는 타입 checking을 안하니까)

타입은 let myName: string ="Alice"; 이런식으로

Contextual Typing

* 익명함수에서도 타입이 추론되기 때문에&#x20;

#### => type 과 interface 의 차이점

[https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#differences-between-type-aliases-and-interfaces](https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#differences-between-type-aliases-and-interfaces)

type aliases

* 이건 진짜 타입 aliases! 같은 타입인데 서로 다른 버전을 만든다 뭐 이런거 안 됨
* string이라는 primitive 타입을 다른 이름으로 바꿔서 쓸 수 있어

interface

* object type에 이름을 주는 방식

차이점

* 두개는 거의 비슷해서 아무거나 골라서 써도 되지만 \
  type은 재생성 안됨, extending 하려면 & intersection으로 할 수는 있음\
  interface는 기존 interface에 새로운 필드를 넣을 수 있음, interface는 extends 가능

#### => react.js 의 본체 type(?) 에 대한 설명

[https://github.com/typescript-cheatsheets/react](https://github.com/typescript-cheatsheets/react)

#### => es6 베이스 + ts 의 type 를 사용하기 (너무 ts 의존적으로 가지 말기)

TypeScript 실행 전 타입 checking을 함으로써 우리가 짜는 로직에서의 런타임 에러 방지

사실 서버에서 잘못 오는 데이터로 발생하는 런타임에러는 어쩔 수가 없음

#### => map = hash = dictionary 로 data 접근하기. (너무 많은 (100개 이상) array 를 loop 돌면서 찾는 방법 지향하기.)

[https://howtodoinjava.com/typescript/maps/](https://howtodoinjava.com/typescript/maps/)

map을 쓰자!!!!! O(1) 의 성능으로 최적화 가능

* [https://medium.com/@bretcameron/how-javascript-maps-can-make-your-code-faster-90f56bf61d9d](https://medium.com/@bretcameron/how-javascript-maps-can-make-your-code-faster-90f56bf61d9d)

#### => vscode 를 써야 하는 이유.. M$

[https://code.visualstudio.com/docs/languages/typescript](https://code.visualstudio.com/docs/languages/typescript)

### next.js 설명

#### => react.js 의 기업에서의 요구 사항 대응 히스토리

[https://reactjs.org/docs/react-dom-server.html](https://reactjs.org/docs/react-dom-server.html)

SSR에 대한 요구는 계속 있어왔고 react에서도 제공했었는데 아주 기본만

#### => next.js 를 만드는 사람들에 대한 히스토리

[https://vercel.com/blog/vercel-welcomes-rich-harris-creator-of-svelte](https://vercel.com/blog/vercel-welcomes-rich-harris-creator-of-svelte)

[https://datastation.multiprocess.io/blog/2021-11-13-benchmarking-esbuild-swc-typescript-babel.html](https://datastation.multiprocess.io/blog/2021-11-13-benchmarking-esbuild-swc-typescript-babel.html)

[https://kdy1.github.io/post/dev/swc/2021/09/new-companies/](https://kdy1.github.io/post/dev/swc/2021/09/new-companies/)

[https://vercel.com/about](https://vercel.com/about)

[https://swc.rs/](https://swc.rs/)

[https://twitter.com/kdy1dev](https://twitter.com/kdy1dev)

#### => react.js 에서 되는데 next.js 에서는 안되는 것..

[https://stackoverflow.com/questions/64188144/next-js-using-css-modules-not-working-as-expected](https://stackoverflow.com/questions/64188144/next-js-using-css-modules-not-working-as-expected)

#### => swr 을 사용해서 서버 call 횟수 줄이기.

[https://min9nim.vercel.app/2020-10-05-swr-intro2/](https://min9nim.vercel.app/2020-10-05-swr-intro2/)

[https://dev.to/thatanjan/7-reasons-why-you-should-use-swr-386e](https://dev.to/thatanjan/7-reasons-why-you-should-use-swr-386e)

#### => useState 로 선언된 state 와 일반적인 local variable 이 다른점.

[https://stackoverflow.com/questions/58252454/react-hooks-using-usestate-vs-just-variables](https://stackoverflow.com/questions/58252454/react-hooks-using-usestate-vs-just-variables)

즉각적으로 데이터가 바뀌지 않는 점.. `useState 는 render 목적으로만 사용.`

#### => ContextAPI 를 쓸까 말까.

[https://leewarrick.com/blog/the-problem-with-context/](https://leewarrick.com/blog/the-problem-with-context/)

#### => Dom 은 한번 쓰고 버리는 것. (추적 하지 않는다.)

[https://blog.logrocket.com/deep-dive-into-react-fiber-internals/](https://blog.logrocket.com/deep-dive-into-react-fiber-internals/)

#### => API call 하기. async 하게.

[https://blog.risingstack.com/asynchronous-javascript/](https://blog.risingstack.com/asynchronous-javascript/)

#### => CSS Framework 소개.

[https://ant.design/](https://ant.design/)

[https://tailwindcss.com/](https://tailwindcss.com/)

\


### 서버 아키텍쳐 설명

#### => 소켓 부터 시작된 간단한 설명과 인증 credential 히스토리

한번 접속 했을때 가급적 많은 데이터를 받는게 유리하나.... 적절한...\
\
[https://velog.io/@dogy/%EC%84%9C%EB%B2%84-%EC%9D%B8%EC%A6%9D.-%EC%BF%A0%ED%82%A4Cookie-%EC%84%B8%EC%85%98Session-%ED%86%A0%ED%81%B0JWT](https://velog.io/@dogy/%EC%84%9C%EB%B2%84-%EC%9D%B8%EC%A6%9D.-%EC%BF%A0%ED%82%A4Cookie-%EC%84%B8%EC%85%98Session-%ED%86%A0%ED%81%B0JWT)

#### => 쿠키 => 쿠키 + 세션 => 토큰 + 세션

[https://tecoble.techcourse.co.kr/post/2021-05-22-cookie-session-jwt/#:\~:text=JWT(JSON%20Web%20Token)%EB%9E%80,%EA%B0%80%20%ED%81%B4%EB%9D%BC%EC%9D%B4%EC%96%B8%ED%8A%B8%EB%A5%BC%20%EC%8B%9D%EB%B3%84%ED%95%A9%EB%8B%88%EB%8B%A4](https://tecoble.techcourse.co.kr/post/2021-05-22-cookie-session-jwt/).\
\
[https://raar.tistory.com/m/48](https://raar.tistory.com/m/48)

#### => 우리 서버 구조 인증 credential 설명

앞단에서 새로운 프리미엄관, 기존 웹으로 보낼지 나눠줌

프리미엄관은 Nextjs / 새로운 서버는 Spring boot로 되어있음

기존 서버에서 로그인하면 jwt 토큰을 받아옴

이 토큰을 새로운 서버에 요청할 때 같이 보냄

새로운 서버에서 Bearer token을 파싱해서 사용

\


[https://kdy1.github.io/post/2021/12/2021/](https://kdy1.github.io/post/2021/12/2021/)\
\
[https://kdy1.github.io/post/2021/11/dev/oss/](https://kdy1.github.io/post/2021/11/dev/oss/)

\
