### 2020-2-26

#### 1.VSCODE MAC 快捷键

```
光标移动
1. 移动到单词的最前面：option + ←
2. 移动到单词最末尾：option + →
3. 将当前行代码移动到上一行：option + ↑
4. 将当前行代码移动到下一行：option + ↓
5. 移动到当前行最前面：cmd + ←
6. 移动到当前行最末尾：cmd + →
7. 花括号之间跳转：cmd + shift + \
8. 移动到文档第一行或最后一行：cmd + ↑ / cmd + ↓
文本选择
基于单词，行，文档的光标操作加上个shift键，就可以移动光标的同时选择文本；例如，选择当前光标所在位置到当前行最前面的代码：cmd + ← + shift
删除操作
1. 删除当前行光标后的所有字符：cmd + fn + delete
2. 删除当前行光标前的所有字符：cmd + delete
3. 删除当前单词光标后的字符：option + fn + delete
4. 把当前单词光标前的字符删除：option + delete
添加注释
1. 注释一行代码：cmd + /
2. 注释一整段代码：option + shift + A
格式化代码
1. 格式化代码：option + shift + F
2. 格式化选中行代码：cmd + K cmd + F
3. 代码缩进：cmd + shift + P
文件、符号、代码之间的快速跳转
1. control+ tab(同时按住)，继续按着control键，松开tab键： 打开当前打开文件的列表，选择要打开文件，松开control就能打开对应文件
2. cmd + P打开最近打开文件列表，同时列表顶部出现搜索框，搜索文件名，回车（enter），可以再当前窗口打开对应文件；使用cmd + enter会在新的编辑器窗口打开这个文件
3. control + G：行跳转，输入对应数字回车，可以跳转到当前文件的当前行
4. cmd + P(输入文件名 + “:” + 行数)：跳转到指定文件的指定行数
5. cmd + shift + O：调出当前文件的符号（函数名等），使用方向键或者搜索，回车，就能跳转到你想要的符号；如果输入“:”可以对当前文件的所有符号进行分类
6. cmd + T：打开多个文件，搜索多个文件中的符号
7. F12：跳转到函数的定义处
8. cmd + F12：跳转到函数的实现位置；注：js中没有接口的概念，定义和实现是相同的，所以js中的F12和Cmd + F12效果是一样的
9. shift + F12：打开函数引用的预览（把光标放在函数或者类上，按shift+F12可以打开一个引用列表和内嵌编辑器）
鼠标操作
1. 在vscode中，单击鼠标左键：把光标移动到响应的位置；双击鼠标左键：将当前光标下的单词选中；三击鼠标左键：选中当前行代码；四次点击鼠标左键：选中整个文档
2. 鼠标左键单击行号：直接选中所在行；选中后，再按着shift，鼠标左键再次选择行：可以选中多行代码
3. 悬停提示窗口：当鼠标移动到某些文件上之后，一会就会显示跟鼠标下文本相关的信息；如果鼠标放在某个函数上，按下cmd时，则能在悬停提示的窗口上看到该函数的实现。
4. 代码的跳转和链接：如果我们把鼠标放在函数上时，函数下方会出现一个下划线，然后当我们按下鼠标左键时，就能跳转到该函数的定义处。cmd + 鼠标左键，跳转到函数、变量定义的地方。当我们再编写Markdown这样的非编程语言的文档时，还可以通过cmd+鼠标左键能打开超级链接

折叠代码
cmd + option + ][

格式化代码

cmd + option + L （同idea）可用于格式化样式

终端使用vs code打开当前文件夹
code .
```

### 2021-5-28

#### 1.webpack开启gzip压缩

```js
const CompressionWebpackPlugin = require('compression-webpack-plugin');
// plugins添加一下插件
new CompressionWebpackPlugin({
  algorithm: 'gzip',
  test: /\.js$/,
  threshold: 10240,
  minRatio: 0.8,
}),
```

#### 2.去除全局的 @bable/polyfill，采用按需加载的方式

```js
{
  "presets": [
    [
      "@babel/preset-env",
      {
        "targets": {
          "esmodules": true // 当指定esmodules后，将忽略浏览器目标环境，结合<script type="module"></script>来使用这样方式，会产生更小的脚本文件
        }
      }
    ],
  ],
  "plugins": [
    [
      "@babel/plugin-transform-runtime",
      {
        "corejs": {
          "version": 3,
          "proposals": true
        }
      }
    ],
  ],
}
```
