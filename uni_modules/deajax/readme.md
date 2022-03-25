### 自用组件，根据van-cell组件的属性和样式，模仿自写的uni组件，用于自家uni项目中不适应其他框架的问题。



1. 纯手写的组件，只是模仿了van-cell组件的属性和样式，并不是官方的代码转换来的。
2. 有些官方属性可能我没写上。
3. 可能有bug，随时修复。
4. 有不属于vancell属性，属于自用的拓展。
5. 部分属性使用了css变量，同vant，可以用变量来覆盖样式。
6. 样式和代码分离，没有样式隔离，注意命名可能造成污染，对应的优点是样式优先级较低，可被轻易覆盖。
7. 默认开启了微信小程序的virtualHost属性（虚拟节点），这个带来的影响尚未确定。



> 内置了remix icon图标



# CellGroup Props

| 参数   | 说明                   | 类型    | 默认值 |
| ------ | ---------------------- | ------- | ------ |
| title  | 分组标题               | string  | -      |
| inset  | 是否展示为圆角卡片风格 | boolean | false  |
| border | 是否显示外边框         | boolean | true   |



# CellGroup Slot
| 名称  | 说明                                              |
| ----- | ------------------------------------------------- |
| title | 自定义title显示内容,，如果设置了title属性则不生效 |



# Cell Props
| 参数        | 说明                           | 类型             | 默认值 |
| ----------- | ------------------------------ | ---------------- | ------ |
| icon        | 左侧图标名称                   | string           | -      |
| title       | 左侧标题                       | [String, Number] | -      |
| title-width | 标题宽度，须包含单位           | String           | -      |
| value       | 右侧内容                       | [String, Number] | -      |
| label       | 标题下方的描述信息             | [String, Number] | -      |
| size        | 单元格大小，可选值为 large     | String           | -      |
| border      | 是否显示下边框                 | boolean          | true   |
| center      | 是否使内容垂直居中             | boolean          | false  |
| url         | 点击后跳转的链接地址           | string           | -      |
| clickable   | 是否开启点击反馈               | boolean          | false  |
| is-link     | 是否展示右侧箭头并开启点击反馈 | boolean          | false  |



# Cell Slot
| 名称       | 说明                                                       |
| ---------- | ---------------------------------------------------------- |
| value      | 自定义value显示内容，如果设置了value属性则不生效           |
| title      | 自定义title显示内容，如果设置了title属性则不生效           |
| label      | 自定义label显示内容，需要设置 use-label-slot属性           |
| icon       | 自定义icon显示内容，如果设置了icon属性则不生效             |
| right-icon | 自定义右侧按钮，默认是arrow，如果设置了is-link属性则不生效 |
| extra      | 自定义右侧额外内容                                         |

