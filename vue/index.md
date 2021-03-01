### 2020-2-26

#### 1.event bus 插件

```js
const bus = function (Vue) {
  const Bus = new Vue({
    methods: {
      emit(event, ...args) {
        this.$emit(event, ...args)
      },
      on(event, callback) {
        this.$on(event, callback)
      },
      off(event, callback) {
        this.$off(event, callback)
      },
    },
  })
  Vue.prototype.$bus = Bus
}
export default bus

// 使用方式：
// main.js
import vueBus from '../libs/bus.js'

Vue.use(vueBus)
```

### 2020-3-1

### 1.vant-js 的 van-dropdown-menu 滚动会穿透到 van-pull-refresh

```
vant@2.3.0修复了此问题，需要升级项目中vant版本，但是升级以后报错\$atters is readonly 或者 \$listeners is readonly.
因为vant-ui新版本里面依赖的vue版本跟当前项目中的vue版本不一致，导致了重复new Vue(),要升级当前版本的vue.
但是升级当前版本vue之后，可能会有一些其他的依赖也要同步更新，比如vue-template-compiler.
```
