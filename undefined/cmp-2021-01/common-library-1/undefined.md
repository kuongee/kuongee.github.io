# 코드 일부

index.js

```javascript
import vueRouter from 'vue-router';
import vueCookie from 'vue-cookie';
import vueI18n from 'vue-i18n';
import lodash from 'lodash';
import moment from 'moment';
import momentTimezone from 'moment-timezone';
import { commonAxios } from './commonAxios';
import eventBus from './eventBus';
import libraryBuilder from './config/libraryBuilder';
import axiosInterceptors from './config/axiosInterceptors';
import messages, { i18nUtil } from './i18n';

const plugin = {
  install(Vue, options = { showAllProgress: true, isUseI18nNRouter: true }) {
    /* Libraries */
    Vue.use(vueCookie);

    if (options.isUseI18nNRouter !== false) {
      Vue.use(vueI18n);
      Vue.use(vueRouter);
    }

    Vue.prototype.$http = commonAxios;
    axiosInterceptors(Vue.prototype.$http, options.showAllProgress);
  },
};

export default plugin;

function initLibrary() {
  return libraryBuilder();
}

/*
  // initLibrary 외부 사용법
  initLibrary().then(function(library) {
    console.log('init cmp-portal-library ', library);
  });
*/

export {
  vueRouter,
  vueI18n,
  lodash,
  moment,
  momentTimezone,
  commonAxios,
  eventBus,
  i18nUtil,
  initLibrary,
  messages,
};

```

