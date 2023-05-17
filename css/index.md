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

#### 3.flex 固定一栏起始宽度

```css
flex: 0 0 200px;
```

```
0 - 不拉长（flex-grow）
0 - 不缩短（flex-shrink）
200px - 开始于 200px (flex-basis),当容器宽度不足200px时，项目会自动缩小，如果容器足够，就保持200px不变，相对于直接对项目设置width:200px，更加的弹性。
```

#### 4.创建一个 BFC(块级格式化上下文) 的方式

```
1.根元素
2.float 不为 none，可以属性设置为 left 或 right
3.overflow 不为 visible，例如 overflow: auto 或 overflow: hidden
4.display:table-cell / table-caption / inline-block / flex / inline-flex
5.position 不为 static 或者 relative，可以属性设置为 absolute 或 fixed
```
