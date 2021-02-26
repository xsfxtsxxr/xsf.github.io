### 2020-2-26

#### 1.文字溢出效果在手机端有时候不显示

```css
text-overflow:ellipsis;
white-space:nowrap;
overflow:hidden;
display:block; 或者inline-block; // 注意添加这一句话
```

```
如果是flex布局，设置flex-grow: 1，会无限拉长item的内容，超出容器所以给该item设置
.content {
  flex: 1;
  width: 0;
}
```

#### 2.固定外层元素不滚动，内层滚动

```css
外层设置 overflow-y:hidden
内层设置 overflow-y:auto, height: 100vh,不要设置min-height
```
