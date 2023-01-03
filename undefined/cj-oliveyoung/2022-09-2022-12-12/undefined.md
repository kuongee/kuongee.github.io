# 라이브관 만들면서 경험했던 것들!

### 1. 신규 프리미엄관과 라이브관 어느 날 부터 PullToRefresh가 안 된다

CSS overscroll-behavior 속성 contain으로 변경

```
// Some code
html, body {
  position: relative;
  height: 100vh;
  overscroll-behavior: contain; // none 이었음
  -webkit-overflow-scrolling: none;
}
```

참고

* [https://mygumi.tistory.com/424](https://mygumi.tistory.com/424)
* [https://developer.mozilla.org/en-US/docs/Web/CSS/overscroll-behavior](https://developer.mozilla.org/en-US/docs/Web/CSS/overscroll-behavior)

### 2. useLayoutEffect라는 친구도 잘 활용해보자

{% embed url="https://medium.com/@jnso5072/react-useeffect-%EC%99%80-uselayouteffect-%EC%9D%98-%EC%B0%A8%EC%9D%B4%EB%8A%94-%EB%AC%B4%EC%97%87%EC%9D%BC%EA%B9%8C-e1a13adf1cd5" %}

### 3. iOS (safari)에서 CSS가 제로 안 먹거나 깜빡이는 문제가 있었음

#### **첫번째** 모서리가 둥글어야 하는데 뾰족함

z-index 값을 0으로 넣어줌

![](<../../../.gitbook/assets/image (2) (1).png>)

사파리에서는 레이아웃이 겹칠 때 요소들의 인덱스를 정확하게 파악하지 못하는 이슈가 있더라구요... 그래서 저런식으로 z 축 값을 한번 조정해줘야 깜빡임이 해소되는것으로 알고 있습니다! \_ 홍수조님

#### 두번째 딤처리 한 영역이 깜빡임

참고 영상

[http://cjics.cj.net/jira/secure/attachment/154807/CJOYLIVE-615.MP4](http://cjics.cj.net/jira/secure/attachment/154807/CJOYLIVE-615.MP4)

| <pre><code>transform: translateZ(0); ---> z-index: 0; 로 수정
</code></pre> |
| ------------------------------------------------------------------------ |

참고

* [https://shynaunum.tistory.com/32](https://shynaunum.tistory.com/32)
* [https://www.sungikchoi.com/blog/safari-overflow-border-radius/](https://www.sungikchoi.com/blog/safari-overflow-border-radius/)



### 4. 이전 페이지로 뒤로 갔는데 왜 useEffect 안 불려?(또 iOS....)

상황 설명: 라이브관에서 상품 상세로 갔다가 다시 라이브관으로 이전 가기 했는데 useEffect 안 불려 → 그래서 하단바를 초기화해주는 코드를 안 타!!!

BFCache...?라는 친구로 의심이 갑니다.

그래서 몇가지 블로그를 참고하여 pageshow 이벤트로 억지로 감지해서 하단바를 노출하게 했습니다.

(하지만 앱에서 수정해주셔서 아래 이벤트를 거치지 않고도 할 수 있게 되었습니다!!!)

| <pre><code>window.addEventListener("pageshow", function (event) {
        if (event.persisted) {
          if (isApp &#x26;&#x26; appInfo.isIos &#x26;&#x26; isIncludePath(LIVE_SHOP)) {
            setNativeUtilBarVisibility(true);
            setLiveNudgeVisibility(false);
          }
        }
      });
</code></pre> |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

참고

* [https://goddaehee.tistory.com/266](https://goddaehee.tistory.com/266)
* [https://velog.io/@kokyunghwan/BFCache](https://velog.io/@kokyunghwan/BFCache)
