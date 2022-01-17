# Storybook의 webpack.config.js 설명

```
const path = require('path');
// 모듈은 개발자가 프로그램을 기능 단위로 쪼개놓은 것을 의미
// 웹팩은 여러 모듈 시스템들처럼 프로젝트에 모듈 컨셉을 적용할 수 있게 해줌
// 웹팩 모듈은 다양한 방법으로 의존성(dependency)를 표현할 수 있음
// 웹팩은 loader를 통해 다양한 언어와 preprocessor들로 작성된 모듈들을 지원
// https://webpack.js.org/concepts/modules/
module.exports = {
 // 모듈을 어떻게 처리할지
 // https://webpack.js.org/configuration/resolve/#resolve
 resolve: {
    alias: { // 파일 경로
      '@': path.join(__dirname, '..', 'src'),
    },
  },
  module: {
    rules: [
      {
        test: /\.(css|scss)$/, // 파일 확장자 체크
        use: [ // 이 로더를 적용해라
          'vue-style-loader',
          'css-loader',
          {
            // https://webpack.js.org/loaders/sass-loader/
            loader: 'sass-loader',
            options: {
              additionalData: `
                    @import "src/assets/scss/style.scss";
                  `,
            },
          },
        ],
        include: path.resolve(__dirname, '..'), // 이 조건에 맞는 모든 모듈을 포함해라
      },
      {
        test: /\.(svg|gif)$/,
        use: [
          {
            // https://webpack.js.org/loaders/url-loader/
            // file을 base64 URI로 변환, 예로 image file을 html 파일에 넣어 하나로 사용할 수 있게 함
            loader: 'url-loader',
            options: {
              esModule: false,
            },
          },
        ],
      },
      {
        test: /\.(woff2?|eot|ttf|otf)(\?.*)?$/,
        use: [
          {
            loader: 'url-loader',
          },
        ],
      },
    ],
  },
};
```

\
참고

[https://webpack.js.org/configuration/](https://webpack.js.org/configuration/)

[https://joshua1988.github.io/webpack-guide/concepts/loader.html](https://joshua1988.github.io/webpack-guide/concepts/loader.html)

[https://stackoverflow.com/questions/34623229/webpack-loaders-and-include](https://stackoverflow.com/questions/34623229/webpack-loaders-and-include)
