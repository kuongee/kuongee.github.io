# CJ올리브영 2차 준비

자기소개

1차 때 답 못했던 질문들

* HTTP1.0 vs HTTPS2.0
* HTTP vs HTTPS
* promise 공부하고 있다고 함 -&gt; **어떤 API...???** 있냐고 물어보심 \(잘 몰라서 그냥 아무거나 대답함\)
  * [https://ko.javascript.info/promise-api](https://ko.javascript.info/promise-api)
  * `Promise` 클래스에는 5가지 정적 메서드가 있습니다.

    1. `Promise.all(promises)` – 모든 프라미스가 이행될 때까지 기다렸다가 그 결괏값을 담은 배열을 반환합니다. 주어진 프라미스 중 하나라도 실패하면 `Promise.all`는 거부되고, 나머지 프라미스의 결과는 무시됩니다.
    2. `Promise.allSettled(promises)` – 최근에 추가된 메서드로 모든 프라미스가 처리될 때까지 기다렸다가 그 결과\(객체\)를 담은 배열을 반환합니다. 객체엔 다음과 같은 정보가 담깁니다.
       * `status`: `"fulfilled"` 또는 `"rejected"`
       * `value`\(프라미스가 성공한 경우\) 또는 `reason`\(프라미스가 실패한 경우\)
    3. `Promise.race(promises)` – 가장 먼저 처리된 프라미스의 결과 또는 에러를 담은 프라미스를 반환합니다.
    4. `Promise.resolve(value)` – 주어진 값을 사용해 이행 상태의 프라미스를 만듭니다.
    5. `Promise.reject(error)` – 주어진 에러를 사용해 거부 상태의 프라미스를 만듭니다.

    실무에선 다섯 메서드 중 `Promise.all`을 가장 많이 사용합니다.

  * 프라미스 메서드 `Promise.resolve`와 `Promise.reject`는 `async/await` 문법\([뒤에서](https://ko.javascript.info/async-await) 다룸\)이 생긴 후로 쓸모없어졌기 때문에 근래에는 거의 사용하지 않습니다.

