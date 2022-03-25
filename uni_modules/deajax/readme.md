
# CellGroup Props
参数	说明	类型	默认值
title	分组标题	string	-
inset v1.7.2	是否展示为圆角卡片风格	boolean	false
border	是否显示外边框	boolean	true

# CellGroup Slot
名称	说明
title	自定义title显示内容，如果设置了title属性则不生效

# Cell Props
参数	说明	类型	默认值
icon	左侧图标名称或图片链接，可选值见 Icon 组件	string	-
title	左侧标题	string | number	-
title-width	标题宽度，须包含单位	string	-
value	右侧内容	string | number	-
label	标题下方的描述信息	string	-
size	单元格大小，可选值为 large	string	-
border	是否显示下边框	boolean	true
center	是否使内容垂直居中	boolean	false
url	点击后跳转的链接地址	string	-
link-type	链接跳转类型，可选值为 redirectTo switchTab reLaunch	string	navigateTo
clickable	是否开启点击反馈	boolean	false
is-link	是否展示右侧箭头并开启点击反馈	boolean	false
required	是否显示表单必填星号	boolean	false
arrow-direction	箭头方向，可选值为 left up down	string	-
use-label-slot	是否使用 label slot	boolean	false

# Cell Slot
名称	说明
value	自定义value显示内容，如果设置了value属性则不生效
title	自定义title显示内容，如果设置了title属性则不生效
label	自定义label显示内容，需要设置 use-label-slot属性
icon	自定义icon显示内容，如果设置了icon属性则不生效
right-icon	自定义右侧按钮，默认是arrow，如果设置了is-link属性则不生效