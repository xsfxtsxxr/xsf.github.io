### 2020-2-26

#### event bus 插件

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
```

**使用方式：**

```js
// main.js
import vueBus from '../libs/bus.js'

Vue.use(vueBus)
```
