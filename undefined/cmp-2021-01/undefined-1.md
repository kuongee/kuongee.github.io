# 빌드 공부

희영 프로님 설명

login에서도 library를 갖고 있고 component에서도 library를 갖고 있고 common에서도 갖고 있음

common에서 빌드하면 library도 빌드해

그런데 login에서도 library를 빌드해서 떨어뜨리는데 library를 서로 다른 모듈 아이디로 가지고 있었음

그래서 이걸 common에서 못 찾는 문제가 생김

\(login이 빌드 될 때 library, login을 따로 떨어트리는데 login에서는 library에 대한 정보를 갖고 있는데 이걸 못 찾음\)

결국 library, login, component, common, container를 모두 dev로 빌드하는데

크롬 console에서 소스코드를 확인할 수 있는 것이 문제 \(구름모양 디렉토리가 있음\)

이것저것 해보시다가 source-map: false로 주셨다.

### 소스맵

소스 맵이란 배포용으로 빌드한 파일과 원본 파일을 서로 연결시켜주는 기능

참고

* [https://joshua1988.github.io/webpack-guide/devtools/source-map.html](https://joshua1988.github.io/webpack-guide/devtools/source-map.html)
* [https://perfectacle.github.io/2016/11/14/Webpack-devtool-option-Performance/](https://perfectacle.github.io/2016/11/14/Webpack-devtool-option-Performance/)

