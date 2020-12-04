---
description: '2020-04-08'
---

# Typescript로 Todo 목록 만들기

### 1. Motivation

Javascript로만 Todo 목록 앱 구현하기에 이어 Typescript로만 Todo 목록 구현하기 진행

### 2. Implementation

* Typescript
  * Javascript Todo 구현할 때 데이터들의 validation을 적용하여 올바른 데이터가 전달되는지 등을 확인
  * Typescript의 경우, 변수에 type을 지정하기 때문에 검증이 가능
* Webpack

  * Webpack으로 번들링해서 하나의 모듈로 사용하기
  * 이 프로젝트에서 필요한 이유
    * .ts 파일 -&gt; .js 파일로 transpile 해서 html 파일에 적용하려고 했더니 module path가 지정되어있지 않아서 \(아래 코드와 같이\) 모듈을 불러오지 못하는 문제가 생기기 때문에 webpack의 필요성을 느낌

  ```text
  // app.ts
  import TodoList from './TodoList';
  ```



