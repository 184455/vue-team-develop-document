# 国际化: i18n

项目中的国际化主要依靠 `i18n` 来完成。

```javascript
import Vue from 'vue'
import VueI18n from 'vue-i18n'
import zh from './language/zh'
import en from './language/en'

Vue.use(VueI18n)

export default new VueI18n({
  locale: 'zh', // 在此切换语言选项
  messages: { en, zh }
})
```

然后在 main.js 中把 i18n 注入到项目的根目录中。具体配置查看[官方GitHub](https://github.com/kazupon/vue-i18n).

> 注意：插件背后依赖 Vuex 的原理实现，你不能去修改 i18n 的数据，否则会报错。

```javascript
import Vue from 'vue'
import App from './App.vue'
import router from './router'
import FastClick from 'fastclick'
import i18n from './i18n/index'
import store from './store'

Vue.config.productionTip = false
new Vue({
  router,
  i18n,
  store,
  render: h => h(App)
}).$mount('#app')

```
