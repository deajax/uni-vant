### 自用组件，根据van组件的属性和样式，模仿自写的uni组件，用于自家uni项目中不适应其他框架的问题。



1. 纯手写的组件，只是模仿了vant组件的属性和样式，并不是官方的代码转换来的。
2. 有些官方属性可能我没写上，要么是因为懒，要么是写不了。
3. 可能有bug，随时修复。
4. 有不属于vant的属性，也有写不了实现不了的功能，仅属自用拓展。
5. 部分属性使用了css变量，同vant，可以用变量来覆盖样式。
6. 样式和代码分离，没有样式隔离，注意命名可能造成污染，对应的优点是样式优先级较低，可被轻易覆盖。
7. 默认开启了微信小程序的virtualHost属性（虚拟节点），这个带来的影响尚未确定。
7. 微信小程序和支付宝小程序都是测试过没问题的，h5样式多少有些小问题，主要是没时间测，有时间了我会改改。支持列表里的x并非都是不支持，填不确定他也显示x。



> 内置了remix icon图标



------

### 以下是文档：

------

**使用方法**

从插件市场下载后配置pages.json文件：

```json
"easycom": {
		"autoscan": true,
		"custom": {
			"^van-(.*)": "@/uni_modules/deajax-ui/components/van-$1/index.vue"
		}
}
```

**图标**

图标使用[Remix icon](https://remixicon.cn/)，

可以直接在van-cell中使用，如：`<van-cell icon="ri-add-line" />`

或者单独使用，如：`<view class="ri-add-line"></view>`

  

**单元格组**

## Cell Group

  

示例：

```vue
<template>
	<van-cell-group title="组标题">
    <van-cell title="单元格" value="内容"></van-cell>
    <van-cell title="单元格" value="内容" label="描述信息"></van-cell>
  </van-cell-group>
</template>
```

  

#### Props

| 参数   | 说明                   | 类型    | 默认值 |
| ------ | ---------------------- | ------- | ------ |
| title  | 分组标题               | String  | -      |
| inset  | 是否展示为圆角卡片风格 | Boolean | false  |
| border | 是否显示外边框         | Boolean | true   |

  

#### Slot
| 名称  | 说明                                              |
| ----- | ------------------------------------------------- |
| title | 自定义title显示内容,，如果设置了title属性则不生效 |

  

  

**单元格**

## Cell 

  

示例：

```vue
<template>
	<van-cell title="单元格" label="描述信息" value="内容"></van-cell>
</template>
```

  

#### Props

| 参数               | 说明                                                       | 类型             | 默认值     |
| ------------------ | ---------------------------------------------------------- | ---------------- | ---------- |
| icon               | 左侧图标名称                                               | String           | -          |
| title              | 左侧标题                                                   | [String, Number] | -          |
| title-width        | 标题宽度，须包含单位                                       | String           | -          |
| value              | 右侧内容                                                   | [String, Number] | -          |
| label              | 标题下方的描述信息                                         | [String, Number] | -          |
| size               | 单元格大小，可选值为 large                                 | String           | -          |
| border             | 是否显示下边框                                             | Boolean          | true       |
| center             | 是否使内容垂直居中                                         | Boolean          | false      |
| url                | 点击后跳转的链接地址                                       | String           | -          |
| clickable          | 是否开启点击反馈                                           | Boolean          | false      |
| is-link            | 是否展示右侧箭头并开启点击反馈                             | Boolean          | false      |
| link-type `v0.1.1` | 链接跳转类型，可选值为 `redirectTo` `switchTab` `reLaunch` | String           | navigateTo |

  

#### Slot
| 名称       | 说明                                                       |
| ---------- | ---------------------------------------------------------- |
| value      | 自定义value显示内容，如果设置了value属性则不生效           |
| title      | 自定义title显示内容，如果设置了title属性则不生效           |
| label      | 自定义label显示内容           |
| icon       | 自定义icon显示内容，如果设置了icon属性则不生效             |
| right-icon | 自定义右侧按钮，默认是arrow，如果设置了is-link属性则不生效 |
| extra      | 自定义右侧额外内容                                         |

  

  

**商品卡片**

## Card

> 商品卡片并未完全按照vant的样式和属性进行编写，只是为了方便实现业务。

   

示例：

```vue
<template>
	<van-card
				title="商品标题"
				desc="描述信息"
				price="2.00"
				num="2"
				thumb="https://via.placeholder.com/150"
				tag="标签"
				clickable
				@click="onClick"
			>
				<view slot="extra">extra</view>
	</van-card>
</template>

<script>
export default {
	methods: {
		onClick() {
			console.log('click card');
		}
	}
};
</script>
```

  

#### Props

| 参数         | 说明                                | 类型             | 默认值                                |
| ------------ | ----------------------------------- | ---------------- | ------------------------------------- |
| layout       | 布局，可选'vertical'                | String           | -                                     |
| title        | 标题                                | String           | -                                     |
| desc         | 描述                                | String           |                                       |
| num          | 商品数量                            | [String, Number] | 1                                     |
| thumb        | 左侧图片 URL                        | String           | -                                     |
| thumb-mode   | 图片模式，同uni image组件的mode属性 | String           | 'aspectFill'                          |
| thumb-size   | 左侧图片尺寸，单位尺寸px            | String           | css定义横向默认80，竖向100%且为正方形 |
| tag          | 图片角标                            | String           | -                                     |
| tag-style    | 图片角标样式                        | Object           | -                                     |
| price        | 商品价格                            | [String, Number] | 0.00                                  |
| origin-price | 商品划线原价                        | [String, Number] | 0.00                                  |
| clickable    | 是否开启点击反馈                    | Boolean          | true                                 |

 

#### Slot

| 名称         | 说明                   |
| ------------ | ---------------------- |
| tag          | 自定义图片角标         |
| thumb        | 自定义图片             |
| top          | 自定义上方区域         |
| title        | 自定义标题             |
| desc         | 自定义描述             |
| tags         | 自定义描述下方标签区域 |
| extra        | 自定义右侧额外内容     |
| bottom       | 自定义下方区域         |
| price        | 自定义价格             |
| origin-price | 自定义商品原价         |
| num          | 自定义数量             |

   

​    

**标签页**

# Tab

> 这个组件太难写了，好多属性实现不了，这个uni和vue和微信小程序都不太一样，凑合用吧。

> <font color=red>**!!!注意：tab必须声明 `name`，`v-model`默认为`String`类型的`1`**</font>

  

示例：

```vue
<template>
  <van-tabs v-model="value">
    <van-tab title="标签1" name="1">内容1</van-tab>
    <van-tab title="标签2" name="2">内容2</van-tab>
    <van-tab title="标签3" name="3">内容3</van-tab>
    <van-tab title="标签4" name="4">内容4</van-tab>
  </van-tabs>
</template>

<script>
export default {
	data() {
		return {
			value: '1',
		};
	}
};
</script>
```

  

#### Tabs Props

| 参数                 | 说明                                                         | 类型             | 默认值 |
| -------------------- | ------------------------------------------------------------ | ---------------- | ------ |
| v-model              | 当前选中标签的标识符                                         | [String, Number] | ‘1’    |
| type                 | 样式风格，可选值为`card`                                     | String           | line   |
| color                | 标签主题色                                                   | String           | -      |
| duration             | 动画时间，单位秒                                             | Number           | 0.3    |
| line-width           | 底部条宽度，默认单位`px`                                     | [String, Number] | 40     |
| line-height          | 底部条高度，默认单位`px`                                     | [String, Number] | 3      |
| animated             | 是否开启切换标签内容时的转场动画                             | Boolean          | false  |
| border               | 是否展示外边框，仅在 `line` 风格下生效                       | Boolean          | false  |
| ellipsis             | 是否省略过长的标题文字                                       | Boolean          | true   |
| sticky               | 是否使用粘性定位布局                                         | Boolean          | false  |
| ~~swipeable~~        | ~~是否开启手势滑动切换~~                                     | 暂不支持         |        |
| ~~lazy-render~~      | ~~是否开启标签页内容延迟渲染~~                               | 暂不支持         |        |
| offset-top           | 粘性定位布局下与顶部的最小距离，单位`px`                     | Number           | -      |
| swipe-threshold      | 滚动阈值，标签数量超过阈值且总宽度超过标<br />签栏宽度时开始横向滚动 | Number           | 5      |
| title-active-color   | 标题选中态颜色                                               | String           | -      |
| title-inactive-color | 标题默认态颜色                                               | String           | -      |
| z-index              | z-index 层级                                                 | Number           | 10     |

  

#### Tab Props

| 参数         | 说明                       | 类型             | 默认值 |
| ------------ | -------------------------- | ---------------- | ------ |
| name (必填)  | 标签名称，作为匹配的标识符 | [String, Number] | '1'    |
| title        | 标题                       | String           | -      |
| ~~disabled~~ | ~~是否禁用标签~~           | 暂不支持         |        |
| dot          | 是否显示小红点             | Boolean          | false  |
| info         | 图标右上角提示信息         | [String, Number] | -      |
| title-style  | 自定义标题样式             | String           | -      |

  

#### Tabs Slot

| 名称      | 说明         |
| --------- | ------------ |
| nav-left  | 标题左侧内容 |
| nav-right | 标题右侧内容 |

  

#### Tab Slot

| 名称 | 说明       |
| ---- | ---------- |
| -    | 标签页内容 |

   

#### Tabs Event

| 名称   | 说明           | 参数                          |
| ------ | -------------- | ----------------------------- |
| @click | 点击标签时触发 | name：标签标识符，title：标题 |

