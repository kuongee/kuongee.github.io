# HTML5 drag and drop

### HTML5 Drag and Drop

* Drag and Drop 기능은 사용자들에게 직관적인 UI를 제공할 수 있다.
  * 예) 파일 업로드, 레이아웃 변경, 아이템 선택 후 타겟 위치에 이동
* HTML5 DnD는 DOM event model과 마우스 이벤트에서 상속된 **drag event**를 사용한다.

#### Drag 이벤트 종류

![](http://confluence.score/download/attachments/81092379/image2019-2-12\_11-4-34.png?version=1\&modificationDate=1550471645000\&api=v2)![](http://confluence.score/download/attachments/81092379/image2019-2-11\_17-1-59.png?version=1\&modificationDate=1549872117000\&api=v2)

* **dragstart**: drag 아이템이 클릭되고 움직이기 시작할 때 발생하는 이벤트
* **drag**: drag 되는 아이템에서 발생하는 이벤트로 drag되는 동안 계속해서 발생하는 이벤트
* **dragend**: drag 아이템에서 drag가 끝나고 발생하는 이벤트 (drop이 되든 안되든 상관없음)\

* **dragenter**: drag 되는 동안 마우스가 어떤 새로운 element에 진입했을 때 발생하는 이벤트
* **dragover**: drag 되는 동안 어떤 element 위에서 마우스가 움직이고 있을 때 발생하는 이벤트 (drag 이벤트와의 차이: 이벤트가 발생하는 element가 다름)
* **dragleave**: dragenter가 불린 element에서 빠져나올 때 발생하는 이벤트
* **drop**: 현재 마우스가 포커싱 된 곳에서 사용자가 drop 했을 때 발생하는 이벤트
* 참고\
  각 이벤트에는 global 좌표(화면)에서 마우스 포인터의 좌표를 받아올 수 있는 **screenX, screenY** 속성을 가지고 있다.\
  Local 좌표(DOM content)의 좌표를 나타내는 **clientX, clientY** 속성도 가지고 있다.

#### 사용방법

Drag 할 아이템을 선택하고 Drop 할 타겟에 이동시킨 후 놓는다.

* **Drag할 대상**
  * Drag할 대상을 **draggable** 아이템으로 설정한다.
  *   Drag 하기 시작했을 때 발생하는 **dragstart** 이벤트의 이벤트 핸들러인 **ondragstart**를 정의한다.

      * dragstart 이벤트 핸들러에서 drag 되는 동안 유지하고 싶은 아이템의 데이터를 저장할 수 있다. (아래 Drag Data 참고)



      ```markup
      <p id="AppleText" draggable="true" ondragstart="onDragStart(event)"> Apple </p>
      ```
* **Drag Data**
  * Drag 되는 아이템의 데이터를 유지할 수 있다.
  *   모든 Drag Event에는 **dataTransfer**라는 property가 있다.\


      * dataTransfer는 데이터의 타입과 데이터의 값 정보를 가진다.
      * 데이터 타입(format)은 MIME Type으로 사용한다.\
        권장하는 데이터 타입([링크](https://developer.mozilla.org/en-US/docs/Web/API/HTML\_Drag\_and\_Drop\_API/Recommended\_drag\_types))\
        &#x20;예) 텍스트는 text/plain을 사용, PNG 이미지는 image/png 사용

      예시) dragstart 이벤트에 대한 핸들러에서 사용 예시

      * dataTransfer 속성에 setData 함수를 이용해 drag하는 아이템의 타입과 데이터 정보를 저장한다.



      ```javascript
      function onDragStart(ev) {
      	ev.dataTransfer.setData("text/plain", ev.target.id);
      }
      ```
*   **Drop 할 타겟**

    * Drag 된 아이템을 drop 하고 싶은 곳은 drop이 허용될 수 있도록 지정해주어야 한다.
      * dragenter/dragover 이벤트의 핸들러를 통해서 drop 타겟을 지정해줄 수 있다. (대부분의 페이지나 어플리케이션에서는 기본적으로 drop 되는 데이터를 받을 수가 없다.)
      * drop 이벤트가 발생하면 drop 된 아이템을 받고 drop 타겟에 넣어준다.
    * dragenter/dragover/drop 이벤트의 핸들러에서 preventDefault() 메소드 관련 내용\

      * dragenter과 dragover 이벤트에서 preventDefault() 메소드를 호출해서 drop이 가능하도록 지정해준다.
      * drop 타겟에서 발생하는 drop 이벤트에서 preventDefault() 메소드를 호출해주어 브라우저가 drop 된 데이터에 대해 기본 처리를 하지 않도록 해야 한다.
        * 예를 들면 Firefox에서는 기본동작으로 link가 drag되면 link를 오픈한다.\
          (실제 예제 프로그램에서 preventDefault() 메소드를 호출해주지 않아도 정상동작하지만 orange라는 텍스트를 drag & drop 하면 orangeText 라는 곳의 새로운 웹페이지를 열었다.)\

      * [https://developer.mozilla.org/en-US/docs/Web/API/HTML\_Drag\_and\_Drop\_API/Drag\_operations#drop](https://developer.mozilla.org/en-US/docs/Web/API/HTML\_Drag\_and\_Drop\_API/Drag\_operations#drop)
    * **(TODO) preventDefault 메소드에 대해  ->다음 스터디 제목으로 정리**\
      \

    * Drop 이벤트가 발생위치에서 drop이 되면 **drop** 이벤트가 발생하며, **ondrop**에 이벤트 핸들러를 정의한다.



    ```javascript
    function onDrop(ev) {
    	var data = ev.dataTransfer.getData("text");
        console.log("Drag drop " + data);
        var child = document.getElementById(data);
        child.style.color = "blue";
        ev.target.appendChild(child);
        ev.preventDefault();
    }

    function onDragOver(ev) {
        ev.preventDefault();
    }

    function onDragEnter(ev) {
        ev.preventDefault();
    }

    ```

```markup
<div
    id="divStyle"
    ondrop="onDrop(event)"
    ondragover="onDragOver(event)"
    ondragleave="onDragLeave(event)"
>
    <b> Drop Target </b>
</div>
```

* 참고) 예제에서 getData 할 때 "text" 의미
  * text는 내부적으로 text/plain으로 처리

간단한 예제소스\
[https://codesandbox.io/s/7zyorq83y1](https://codesandbox.io/s/7zyorq83y1)

#### Reference

* HTML5 DnD 내부 동작 상세 소개
  * [http://apress.jensimmons.com/v5/pro-html5-programming/ch9.html](http://apress.jensimmons.com/v5/pro-html5-programming/ch9.html)
  * [https://www.w3.org/TR/2010/WD-html5-20101019/dnd.html](https://www.w3.org/TR/2010/WD-html5-20101019/dnd.html)
* HTML5 DnD 기본 소개
  * [https://developer.mozilla.org/en-US/docs/Web/API/HTML\_Drag\_and\_Drop\_API](https://developer.mozilla.org/en-US/docs/Web/API/HTML\_Drag\_and\_Drop\_API)
  * [http://tcpschool.com/html/html5\_api\_dragAndDrop](http://tcpschool.com/html/html5\_api\_dragAndDrop)
* HTML5 DnD 예제
  * [https://www.webdesignerdepot.com/2013/08/how-to-use-html5s-drag-and-drop/](https://www.webdesignerdepot.com/2013/08/how-to-use-html5s-drag-and-drop/)
  * [https://www.html5rocks.com/en/tutorials/dnd/basics/](https://www.html5rocks.com/en/tutorials/dnd/basics/)
  * [https://www.w3schools.com/HTML/html5\_draganddrop.as](https://www.w3schools.com/HTML/html5\_draganddrop.asp)
