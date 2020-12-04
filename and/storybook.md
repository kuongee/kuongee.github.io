---
description: Vue 프로젝트에 스토리북 적용하기
---

# Storybook 적용하기



## 스토리북 <a id="id-[GOV2]Storybook-&#xC2A4;&#xD1A0;&#xB9AC;&#xBD81;"></a>

메인 프로젝트 앱과 독립적으로 띄우고 UI 컴포넌트를 독립적으로 개발하고 보여줄 수 있도록 도와준다.

## Manual Setup <a id="id-[GOV2]Storybook-ManualSetup"></a>

### Step 1: Add dependencies <a id="id-[GOV2]Storybook-Step1:Adddependencies"></a>

```text
npm install @storybook/vue --save-dev
npm install vue-loader vue-template-compiler @babel/core babel-loader babel-preset-vue --save-dev
```

### Step 2: Add an npm script <a id="id-[GOV2]Storybook-Step2:Addannpmscript"></a>

package.json에 다음 스크립트 추가

```text
{
"scripts": {
  "storybook": "start-storybook"
}
}
```

### Step 3: Create the main file <a id="id-[GOV2]Storybook-Step3:Createthemainfile"></a>

.storybook/main.js에 다음 코드 추가

```text
module.exports = {
  stories: ['../src/**/*.stories.[tj]s'],
}
```

### Step 4: Create the webpack config file <a id="id-[GOV2]Storybook-Step4:Createthewebpackconfigfile"></a>

.storybook/webpack.config.js에 다음 코드 추가

* 스토리북 실행 시 생기는 에러에 대해 rule을 추가

```text
const path = require('path');
 
module.exports = {
  resolve: {
    alias: {
      '@': path.join(__dirname, '..', 'src'),
    },
  },
  module: {
    rules: [
      {
        test: /\.(css|scss)$/,
        use: [
          'vue-style-loader',
          'css-loader',
          {
            loader: 'sass-loader',
            options: {
              additionalData: `
                    @import "src/assets/scss/style.scss";
                  `,
            },
          },
        ],
        include: path.resolve(__dirname, '..'),
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

### \(Step 5\): 선택적 추가사항 <a id="id-[GOV2]Storybook-(Step5):&#xC120;&#xD0DD;&#xC801;&#xCD94;&#xAC00;&#xC0AC;&#xD56D;"></a>

```text
npm i -D @storybook/addon-actions
npm i -D @storybook/addon-knobs
```

.storybook/main.js에 아래 코드 추가

```text
module.exports = {
  stories: ['../stories/**/*.stories.[tj]s'],
  addons: ['@storybook/addon-actions', '@storybook/addon-knobs'],
};
```

vue-router를 사용하는 컴포넌트에 대한 스토리를 작성하기 위해 아래 추가

```text
npm install --save-dev storybook-vue-router
```

.storybook/config.js에서 decorator로 등록

```text
import { addDecorator } from '@storybook/vue';
import StoryRouter from 'storybook-vue-router';
 
addDecorator(StoryRouter());
```

### 실행 <a id="id-[GOV2]Storybook-&#xC2E4;&#xD589;"></a>

```text
npm run storybook
```

### 고려해볼 점 <a id="id-[GOV2]Storybook-&#xACE0;&#xB824;&#xD574;&#xBCFC;&#xC810;"></a>

stories 디렉토리 구조를 어떻게 가져갈 것인가

* 앱 소스코드 디렉토리와 같이 위치하게 할것인지
* **stories 디렉토리로 따로 빼낼 것인지 → 앱 소스와 분리해서 복잡하지 않게**

### 참고 <a id="id-[GOV2]Storybook-&#xCC38;&#xACE0;"></a>

* [https://storybook.js.org/docs/guides/guide-vue/](https://storybook.js.org/docs/guides/guide-vue/)
* [https://narusas.github.io/2018/04/08/Storybook-with-vue.html](https://narusas.github.io/2018/04/08/Storybook-with-vue.html)
* Vue-cli로 생성한 프로젝트는 vue-cli-plugin-storybook으로도 설정 가능

