# Webpack ESLint, Prettier 설정

Common Library 소스코드 관리를 위해 ESLint와 Prettier를 설정해보기

### ESLint

ECMAScript 코드에서 문제점을 검사하고 더 나은 코드로 정정하는 린트 도구이다.

* 포맷팅: 일관된 코드 스타일 유지하도록, 가독성 높이는 코드 (들여쓰기 규칙, 코드 라인 최대 너비 규칙 등)
* 코드 품질: 잠재적인 오류나 버그 예방을 위함 (사용하지 않는 변수 등)

#### 설치 및 실행

1. ESLint 설치\
   npm install -D eslint
2. 환경설정 파일 생성\
   .eslintrc.js

```
module.exports = {}
```

이번 common library 프로젝트에서는 **package.json**에 아래와 같이 설정해주었다.

```
"eslintConfig": {
	"env": {
      "es6": true,
      "browser": true,
      "node": true
    },
    "extends": [
      "eslint:recommended",
      "plugin:prettier/recommended"
    ],
    "parserOptions": {
      "ecmaVersion": 2020, // --> 변경
      "sourceType": "module",
      "parser": "babel-eslint"
    },
    "rules": {
      "no-unused-vars": "warn"
    }
}
```

3\. eslint 실행해보기 \
다른 블로그에서 소개해준 방법처럼 해도 되고

```
npx eslint src
```

common library에서는 package.json scripts에 아래와 같이 추가해주었다.

```
"scripts": {
    "build:dev": "npm run lint && webpack --mode development",
    "lint": "eslint src"
}
```

#### ESLint 규칙

[https://eslint.org/docs/rules/](https://eslint.org/docs/rules/)

기본적으로 규칙은 적용되어있지 않지만 'eslint:recommended'로 미리 정해놓은 규칙을 활성화할 수 있다.

```
"extends": [
  "eslint:recommended"
],
```

### Prettier

일관적인 스타일로 코드를 다듬고 ESLint와는 다르게 코드 품질과 관련된 기능은 하지 않는다.

#### 설치 및 실행

1. ESLint와 마찬기지로 prettier 설치\
   npm install -D prettier
2. (여기서는 직접 실행하는 방법은 다루지 않는다. 개인적으로는 VSCode의 formatOnSave로 자동 포맷팅이 되게 하는 것을 선호한다.)
3. Common Library에서는 .prettierrc에 프로젝트 포맷팅 규칙을 정의

### ESLint와 Prettier 통합하기

Prettier만으로도 보기 좋은 코드로 일관되게 관리할 수 있다. 하지만 코드 품질과 관련된 검사는 ESLint가 해주어야 하기 때문에 같이 사용하는 편이 낫다. 그래서 이 둘을 동시에 사용할 때는 규칙이 충돌하지 않도록 해야한다.

이 때 사용할 패키지가 eslint-config-prettier이다.

1. 패키지를 설치

```
npm i -D eslint-config-prettier
```

ESLint 설정 파일의 extends 배열에 추가

```
"extends": [
  "eslint:recommended",
  "eslint-config-prettier"
],
```

이렇게 추가하게 되면 Prettier와 중복되는 ESLint 규칙은 비활성화하여 중복된 포맷팅 규칙은 Prettier가, 나머지 코드의 품질에 대한 검사는 ESLint가 하게 한다.

2\. eslint-plugin-prettier 플러그인\
Prettier 규칙을 ESLint 규칙으로 추가하는 플러그인으로 Prettier의 모든 규칙이 ESLint로 들어오기 때문에 **ESLint만 실행하면 된다**고 한다.

```
npm i -D eslint-plugin-prettier
```

```
"extends": [
  "eslint:recommended",
  "eslint-config-prettier"
],
plugins: [
  "prettier"
],
rules: {
  "prettier/prettier": "error"
}
```

3\. 위의 config와 plugin을 한방에 적용하기

```
"extends": [
  "eslint:recommended",
  "plugin:prettier/recommended" // 이 부분만 추가하면 끝
]
```

### 프로젝트에서 실행하기

Common library 프로젝트는 여러 팀원들이 함께 개발하고 사용하는 프로젝트이기 때문에 일관된 코드와 완성도를 높이기 위해 ESLint + Prettier의 도움이 꼭 필요하다. 팀원들이 코드를 공유할 때 검사를 빠뜨리지 않도록 자동으로 검사하는 것이 필요했다.

다른 블로그에서 소개해준 husky를 활용하여 커밋 전에 검사하는 것도 고려해보았으나 그냥 빌드할 때마다 검사할 수 있게 script를 추가해주었다. 아래처럼 정의해주어 개발계 빌드 시 꼭 린트 검사를 거치고 결과를 확인하도록 했다.

```
"scripts": {
    "build:dev": "npm run lint && webpack --mode development",
    "lint": "eslint src"
}
```



### 참고

* [https://jeonghwan-kim.github.io/series/2019/12/30/frontend-dev-env-lint.html](https://jeonghwan-kim.github.io/series/2019/12/30/frontend-dev-env-lint.html)
* [https://blog.doitreviews.com/development/2020-05-07-babel-eslint-prettier/](https://blog.doitreviews.com/development/2020-05-07-babel-eslint-prettier/)

