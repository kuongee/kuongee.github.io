---
description: Vue를 활용해 웹 페이지 개발할 때 알아두면 좋은 것들 정리
---

# \[Vue\] 궁금 + 알아두면 좋은 것들

#### lodash 사용할 때

사용할 함수만 import 해서 넣는 것을 권장  
예를 들어 reduce를 쓴다. → import { reduce } from 'lodash';  
왜냐하면 나중에 패키지할 때 import \_ from 'lodash'; 이런식으로 하면 불필요한 애들까지 전부 들어온다.  
최적화 시켜주기

#### compute vs. data의 차이?

compute는 데이터가 어딘가 캐시되어 사용되고 있음

#### $nextTick

언젠가 필요할 때가 있다.

#### ref

.

#### v-show vs. v-if

* v-show는 display: none으로 만들어주고
* v-if는 아예 돔에서 넣고 빼고를 제어

#### webpack

* vendor.js 
* treeshaking

#### debounce

* 예 입력 이벤트를 모아서 처리하겠다
* 보통 200~300을 줌

#### &lt;slot&gt;

```text
// A라는 컴포넌트
<div>
	<slot> </slot>
</div>

// A를 이렇게 사용한다면 button이 슬롯 자리로 쏙 들어가게 함
<A>
	<button />
</A>
```

named slot이라는 것도 있음

#### event - change vs. input

* change는 blur 될 때 ? \(확인 필요\)
* input은 인풋이 계속 바뀔 때

#### mount / create

.

#### array destructure도 알아두기

.

#### v-model

```text
<input :value="a" @input="onchage"/>
<!-- 위 아래 똑같아 -->
<input v-model="a" />
```

#### emit

부모한테 이벤트 보낼 때

emit\('input-text', \_\_\_\_\_\_\_\)

Vue 문서에서 input-text 이런식으로 쓰라고 권장하고 있음 \(inputText 보다\)

#### set

object가 깊어서 rerendering이 안 되는 경우가 있을 때 set으로 변경을 추적

```text
data() {
	a: { b: { c: { d { ....
		} } } }
}
```

[https://kr.vuejs.org/v2/guide/reactivity.html](https://kr.vuejs.org/v2/guide/reactivity.html)

