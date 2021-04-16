### 2021-4-14

#### 1.ANTV-G6 的画布在切换页面后，canvas 画布丢失，导致无法重新绘图问题

```
// 1.如果用的是class component，就在componentWillUnmount里面重置数据
componentWillUnmount(){
  graph = null
  nodes = []
  edges = []
}
// 2.如果用的是function component，就在useEffect里面清除，第二参数空数组，相当于componentDidMount，只开始执行一次，里面return相当于componentWillUnmount
useEffect(() => {
  // ....
  return () => {
    graph = null
    nodes = []
    edges = []
  }
},[])

// 这样一来，再次进入页面的时候会重新调用graph = new G6.Graph({...})，重新生成canvas画布
```

### 2021-4-16

#### 1.ANTV G6 在 React 注册事件会频繁触发问题

```js
// 问题描述:react函数组件中，在useEffect里面注册的graph = new G6.graph，graph.on('node:click',()=>{...})
export default function MapComponent() {
  let graph = null
  useEffect(() => {
    graph = new G6.graph({})
    // 如果在这边注册事件，就会变化一次注册一次事件，比如多加一个node
  }, [nodes, edges])

  // 必须重新写一个useEffect[]来为graph仅注册一次事件
  useEffect(()=>{
    graph.on('node:click',()=>{...})
  },[])
}

```
