# 적용하는 과정에서 마주쳤던 문제들

Vue 프로젝트에 Storybook 적용하기

* Vue cli로 설정된 프로젝트

## Manual Setup으로 해보기

```text
npm install @storybook/vue --save-dev
npm install babel-preset-vue --save-dev 
```

스크립트 추가

* npm storybook

.storybook/webpack.config.js

```text
const path = require('path');
const SRC_DIR = path.resolve(__dirname, '..', 'src');
 
module.exports = {
  resolve: {
    alias: {
      '@': path.join(SRC_DIR),
    },
  },
  module: {
    rules: [
      {
        test: /\.(scss|css)$/,
        use: [
          'vue-style-loader',
          'css-loader',
          {
            loader: 'sass-loader',
            options: {
              additionalData: `@import "assets/scss/mixin/_mixin.scss";`,
            },
          },
        ],
        include: path.join(SRC_DIR, 'assets'),
      },
      {
        test: /\.(svg|gif)$/,
        use: [
          {
            loader: 'url-loader',
            options: {
              esModule: false,
            },
          },
        ],
      },
    ],
  },
};
```

.storybook/config.js

```text
import { configure } from '@storybook/vue';
 
function loadStories() {
  const req = require.context('../src/components', true, /\.stories\.js$/);
  req.keys().forEach(filename => {
    req(filename);
  });
}
 
configure(loadStories, module);
```

이렇게 했는데 vue-loader가 vue 파일 안의 아래 코드를 파싱할 수 없다? 는 메시지가 뜨고 다른 loader가 필요할 수도 있다는 에러 메시지가 뜨면서 제대로 스토리가 보이지 않는 문제가 있었음

## Vue-cli-plugin 으로 해보자 <a id="Storybook-Vue-cli-plugin&#xC73C;&#xB85C;&#xD574;&#xBCF4;&#xC790;"></a>

[https://www.npmjs.com/package/vue-cli-plugin-storybook](https://www.npmjs.com/package/vue-cli-plugin-storybook)

The webpack config used for storybook is resolved from `vue-cli-service`, which means you don't need to have any special `webpack` section in storybook config folder.

```text
vue add storybook
```

vue-cli-plugin

Vue CLI uses a plugin-based architecture. If you inspect a newly created project's `package.json`, you will find dependencies that start with `@vue/cli-plugin-`.

Plugins can modify the internal webpack configuration and inject commands to `vue-cli-service`. Most of the features listed during the project creation process are implemented as plugins.

The plugin based architecture makes Vue CLI flexible and extensible. If you are interested in developing a plugin, check out the [Plugin Development Guide](https://cli.vuejs.org/dev-guide/plugin-dev.html).





--&gt; 결론적으로

```text
const path = require('path');
 
module.exports = {
  module: {
    rules: [{
      test: /\.(css|scss)$/,
      use: [
        'vue-style-loader',
        'css-loader',
        'sass-loader',
      ],
      include: path.resolve(__dirname, '../')
    }]
  }
}
```

