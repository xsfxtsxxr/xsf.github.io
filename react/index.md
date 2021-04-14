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
