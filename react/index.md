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
### 2021-4-23

#### 1.ANTD Notification通知提醒框中的文字不换行

```js
// 添加样式：white-space:pre-line, normal模式下\n会转变为空格
const openNotification = () => {
  notification.open({
    message: 'Notification Title',
    description:
      'This is the content of the notification. \n This is the content of the notification.',
    className: 'custom-class',
    style: {
      whiteSpace: 'pre-line',
    },
  });
};

```

### 2021-5-28

#### 1.formitem 里面的input输入框每次输入一个字符就会失去焦点

```
1.先检查是否给formitem添加了唯一key
2.检查是否因为input的onChange事件做了setState操作，重复更新了input的数据
```

### 2021-6-4

#### 1.React-router嵌套路由

```
1.嵌套路由的重点在于，嵌套路由，不能在父级加 exact(精准匹配)，因为先要匹配 父级 然后才能匹配 子集
2.比如：/nested/a ， 会先匹配父级 /nested 后才能匹配 /nested/a
```