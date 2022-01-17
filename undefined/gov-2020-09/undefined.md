# 프론트 빌드 배포



웹팩 개발 서버

* 게다가 ajax 방식의 api 연동은 cors 정책 때문에 반드시 서버가 필요하다.\
  개발용 서버를 제공해준다.\
  웹팩 서버는 파일 변화를 감지하면 웹팩 빌드를 다시 수행하고 브라우져를 리프레시하여 변경된 결과물을 보여준다.\
  \
  해결하는 방법은 두 가지인데 먼저 서버측 솔루션 부터 보자. 해당 api 응답 헤더에 "Access-Control-Allow-Origiin: \*" 헤더를 추가한 뒤 응답하면, 브라우져에서 응답 데이터를 받을 수 있다.\
  서버 응답 헤더를 추가할 필요없이 웹팩 개발 서버에서 api 서버로 **프록싱**하는 것이다. 웹팩 개발 서버는 [proxy](https://webpack.js.org/configuration/dev-server/#devserverproxy) 속성으로 이를 지원한다.\
  \
  [https://jeonghwan-kim.github.io/series/2020/01/02/frontend-dev-env-webpack-intermediate.html](https://jeonghwan-kim.github.io/series/2020/01/02/frontend-dev-env-webpack-intermediate.html)
*   Vue에서 예를 들어

    프론트를 빌드해서 개발서버에 띄울 때 9090에 떠있을 때\
    → 프론트에서 요청 보낼 때 172.xxx.xxx.xxx:9090/rest 로 요청을 보내는데\
    이때 프록시의 target으로 바뀌어서 가도록

```
// vue.config.js
devServer: {
    disableHostCheck: true,
    proxy: {
      '/': {
        target: 172.xxx.xxx.ooo:8080, // 서버 주소
        changeOrigin: true,
      },
    },
  },
```

dist/

* 프론트를 빌드하면\
  dist/index.html, ....js, ....css 이렇게 떨어지고 이거를 dev 서버에서 실행시키듯이 Apache, nginx 같은데서 띄운다\
  Apache가 html을 띄워

Apache

* httpd.conf 파일에서도 proxy 설정 가능
