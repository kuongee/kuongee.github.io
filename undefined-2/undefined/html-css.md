# HTML, CSS

* innerHTML

  | 장점 | 단점 |
  | :--- | :--- |
  | DOM 조작 방식에 비해 빠르고 간편하다. | XSS공격에 취약점이 있기 때문에 사용자로 부터 입력받은 콘텐츠\(untrusted data: 댓글, 사용자 이름 등\)를 추가할 때 주의하여야 한다. |
  | 간편하게 문자열로 정의한 여러 요소를 DOM에 추가할 수 있다. |  |

  * [https://gist.github.com/caike/35522c3da161d29fc2ce](https://gist.github.com/caike/35522c3da161d29fc2ce)
  * The following code will not trigger an alert. `target.innerHTML = "<script> alert('XSS Attack'); </script>";`

    The following code will trigger an alert. `target.innerHTML = "<img src=x onerror=\"alert('XSS Attack')\" >";`

  * [https://developer.mozilla.org/en-US/docs/Web/API/Element/innerHTML](https://developer.mozilla.org/en-US/docs/Web/API/Element/innerHTML)

* DOM
  * 문서에 접근하고 관리할 수 있는 API로 볼 수 있다. 문서를 브라우저가 이해할 수 있도록 메모리에 올려야 하는데 웹 문서를 브라우저가 이해할 수 있는 구조록 구성하는데 DOM이라고 한다. 요소들이 각각의 객체가 되고 객체들의 구조는 트리 형태이다.

![](../../.gitbook/assets/image%20%2831%29.png)

* HTML 렌더링 과정
  * > **웹 브라우저의 HTML문서 렌더링 과정**

    **1. 불러오기**

    로더\(Loader\)가 서버로부터 전달 받는 리소스 스트림을 읽는 과정.

    읽으면서 어떤 파일인지, 데이터인지 파일을 다운로드할 것인지 등을 결정한다.

    **2. 파싱 \(Phasing\)**

    웹 엔진이 가지고 있는 HTML/XML 파서가 문서를 파싱해서 DOM Tree를 만든다.

    **3. 렌더링 트리 만들기**

    DOM Tree는 내용을 저장하는 트리로 자바스크립트에서 접근하는 DOM객체를 쓸 때 이용하는 것이고 별도로 그리기 위한 트리가 만들어져야 하는데 그것이 렌더링 트리다. \(그릴 때 필요없는 head, title, body태그등이 없음 + display:none 처럼 DOM에는 있지만 화면에서는 걸러내야할 것들을 걸러냄\)

    **4. CSS 결정**

    CSS는 선택자에 따라서 적용되는 태그가 다르기 때문에 모든 CSS 스타일을 분석해 태그에 스타일 규칙이 적용되게 결정한다.

    **5. 레이아웃**

    렌더링 트리에서 위치나 크기를 가지고 있지 않기 때문에 객체들에게 위치와 크기를 정해주는 과정을 레이아웃이라고 함.

    **6. 그리기**

    렌더링 트리를 탐색하면서 그리기.

    \* 참고로 렌더링 엔진은 가능하면 HTML문서가 파싱될 때까지 기다리지 않고, 배치와 그리기 과정을 시작한다.  
  
    출처: [https://jeong-pro.tistory.com/90](https://jeong-pro.tistory.com/90) \[기본기를 쌓는 정아마추어 코딩블로그\]

  *  렌더링 엔진은 HTML 문서를 파싱하고 "콘텐츠 트리" 내부에서 태그를 [DOM](http://www.html5rocks.com/en/tutorials/internals/howbrowserswork/) 노드로 변환한다. 그 다음 외부 CSS 파일과 함께 포함된 스타일 요소도 파싱한다. 스타일 정보와 HTML 표시 규칙은 "[렌더](http://www.html5rocks.com/en/tutorials/internals/howbrowserswork/) [트리](http://www.html5rocks.com/en/tutorials/internals/howbrowserswork/)"라고 부르는 또 다른 트리를 생성한다. [https://d2.naver.com/helloworld/59361](https://d2.naver.com/helloworld/59361)
  * HTMl 파싱 중 스크립트 태그를 만나는 순간부터는 이 스크립트를 로드하고 실행한다. 이 말은 스크립트 태그 뒤쪽에 있는 페이지의 요소들은 그려지지 못하고 앞쪽 스크립트의 로드/실행이 끝날 때까지 기다려야 한다.

![](../../.gitbook/assets/image%20%2827%29.png)



* DOMContentLoaded와 load event 비교
  * **DOMContentLoaded**: 브라우저가 HTML 전부 로드되고 DOM 트리를 완성하는 즉시 발생한다. \(이미지, 스타일 등의 외부 자원들은 기다리지 않는다.\)
    * DOM이 준비되었기 때문에 DOM 노드에 접근이 가능
    * document 객체에서 실행
  * **load**: DOM 트리도 완성되고 외부 자원도 모두 불러오는 것이 끝났을 때 발생한다.
    * 이미지 크기, 스타일 적용 후 실제 요소의 크기 확인 등이 가능
    * window 객체에서 실행
  * **beforeunload/unload**: 사용자가 페이지를 떠날 때 발생한다.
    * beforeunload는 예시로 '정말 이 페이지를 나가시겠습니까?' 이런 체크를 할 때 사용할 수 있다.
    * window 객체에서 발생
* 브라우저에 url을 입력하면 일어나는 일
  * [https://owlgwang.tistory.com/1](https://owlgwang.tistory.com/1)

