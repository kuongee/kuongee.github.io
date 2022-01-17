---
description: 개발환경을 세팅할 때는 디버깅 환경도 중요하다.
---

# \[VSCode] 디버깅 하기

{% embed url="https://code.visualstudio.com/docs/editor/debugging" %}
Visual Studio Code 문서&#x20;
{% endembed %}

### 디버깅 하기 예시 (Node.js 환경)

#### 1) launch.json 파일 작성하기

launch.json은 디버깅을 설정하고 저장하는 파일이며 .vscode 폴더 내부에 저장된다.\
\- VSCode \[Debug] 탭에서 설정 버튼(빨간색 사각형)을 눌러 'launch.json'파일을 연다.\
\- 또는 파란색 사각형의 세모 버튼을 눌러 열어 configuration을 추가할 수도 있다.

![기본 Node.js 의 디버깅 설정](<../.gitbook/assets/image (15).png>)

#### 2)  Configuration 추가해보기

여기서는 Electron 어플리케이션에 대한 설정을 추가하여 디버깅을 진행해본다.\
[https://electronjs.org/docs/tutorial/debugging-main-process-vscode](https://electronjs.org/docs/tutorial/debugging-main-process-vscode)

![](<../.gitbook/assets/image (13).png>)

Attribute 설명

* cwd:  지정한 디렉토리에서 dependency와 다른 파일들을 찾도록&#x20;
* runtimeExecutable: runtime executable의 절대 경로, default는 node
* program: 디버깅할 Node.js 프로그램의 절대 경로 (executable or file to run when launching the debugger)
* outputCapture: std로 설정하여 출력 결과가 Debug console에 출력되게 함

[https://code.visualstudio.com/docs/nodejs/nodejs-debugging](https://code.visualstudio.com/docs/nodejs/nodejs-debugging)

참고: arg 설정도 가능

#### 3) 디버깅 하기

원하는 디버깅 설정을 선택하고 실행해본다.

![실행 화면](<../.gitbook/assets/image (8).png>)
