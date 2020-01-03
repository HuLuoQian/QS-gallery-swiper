
# QQ交流群: 750104037 [点我加入](https://jq.qq.com/?_wv=1027&k=5OyZoXa)

## 可直接拖进示例项目运行
## 若要预览nvue项目，将示例项目中pages/index/index文件后缀修改为nvue运行即可

## 作者想说
如果该插件有什么问题还请大家说出来哦，还有如果有什么建议的话也可以提下呐 ~
如果觉得好用，可以回来给个五星好评么\~\~ (❁´◡`❁)*✲ﾟ*  蟹蟹\~拜托啦\~

---
## 组件简介
swiper图片展示组件, 由 小伙伴付费 定制

# 兼容性
全端. 字节跳动小程序未测试

# 注意
在组件文件夹中有两组相同文件名但后缀不同(vue、nvue)<br />
其实他们的代码是相同的，只不过为了示例项目演示方便而保留两组<be />
在实际应用中将其中一组删除即可，而后根据项目是vue页面还是nvue页面修改后缀名

# 更新说明
| 版本|  说明|
| --------- |  --: |
| v1.4 | 修复vue页面点击事件无效问题，完善有关nvue文档|
| v1.3 | 支持nvue/uni-app编译模式, 相关文档迟一点完善, 若要预览nvue示例, 将示例项目中的pages/index/index文件后缀改为nvue即可|
| v1.2 | 新增top属性，可控制图片距离顶部位置|
| v1.1 | 修复有关z-index层级问题|

# <span id="props">1.`属性总纲`</span>

| 属性| 是否必填|  值类型| 默认值| 说明|
| --------- | -------- | -----: | --: | --: |
| images| | Array<String\|Object> | | 图片数组, 详见[1.0.1](#image)|
| height| | String| `500`| 组件高度, `单位跟随unit`|
| visibleNum| | String\|Number | -1| 当前项左右两边可见数量, 小于等于0则全部可见|
| space| | String\|Number | 10| 图片间距, 单位`%`|
| defCurrent| | String\|Number | 0| 默认初始当前项|
| imageWidth| | String\|Number | `450`| 图片宽度, `单位跟随unit`|
| imageHeight| | String\|Number | `250`| 图片高度, `单位跟随unit`|
| imageBorderRadius| | String | `8`| 图片倒角, `单位跟随unit`|
| defBlur| | Boolean | `false`| 非当前项是否高斯模糊, `nvue不支持`|
| autoplay| | Boolean | `false`| 是否自动轮播|
| interval| | String\|Number | `3000`| 自动轮播时间间隔|
| mask| | Boolean | `vue: false, nvue: true`| 非当前项是否开启遮罩层|
| maskColor| | String | `rgba(0,0,0,.3)`| 遮罩层颜色|
| showControl| | Boolean | `false`| 是否显示左右切换按钮控制|
| indicatorDots| | Boolean | `false`| 是否开启面板指示点, `目前nvue不支持`|
| indicatorDotsConfig| | Object | | 面板指示点样式配置, 详见[1.0.2](#indicatorDotsConfig), `目前nvue不支持`|
| sensitivity| | String\|Number | `20`| 滑动灵敏度（越低越灵敏）|
| defReady| | Boolean | `false`| 初始ready值, 若为false则初始化组件时会有预备进入对应位置的动画|
| duration| | String\|Number | `.2`| 整体过渡动画时长, `nvue不支持`|
| scale| | String\|Number | `0`| 图片各级之间的高度差, 单位`跟随unit`|
| imageBackground| | Boolean | `false`| 背景是否为当前图片|
| unit| | String | `rpx`| 组件使用css单位|
| changeReset| | Boolean | `false`| images改变时是否展示重置视图动画, 时间为(duration*10)秒|
| galleryId| | String\|Object | | 自定义标识用于imageContent判断|
| zIndex| | String\|Number | `999`| z-index属性, `nvue不支持`|
| top| | String\|Number | ~~50%~~`50`| 距离顶部位置，以图片中心计算，换算成组件高度的一半(50%)|
| `1.4新增`| |  |  | |
| topUnit| | String | `vue:%, nvue: rpx`| 距离顶部位置的单位|
| width| | String\|Number | `750`| 组件宽度, 单位跟随unit, `vue不传此参数由外部view控制宽度`|
| autoReady| | Boolean | true| 是否自动设置ready参数为true|

## <span id="image">1.0.1 images属性说明 -> [属性总纲](#props) </span>
| 属性| 是否必填|  值类型| 默认值| 说明|
| --------- | -------- | -----: | --: | --: |
| path| 是| String| | 图片地址|
| backgroundColor| | Color| | 组件背景颜色|

## <span id="indicatorDotsConfig">1.0.2 indicatorDotsConfig属性说明 -> [属性总纲](#props) </span>
| 属性| 是否必填|  值类型| 默认值| 说明|
| --------- | -------- | -----: | --: | --: |
| left| | Number| | 绝对定位的left值|
| bottom| | Number| | 绝对定位的bottom值|
| height| | String| `50rpx`| 高度|
| width| | String| `100%`| 宽度|
| backgroundColor| | Color| `100%`| 背景颜色|
| actItemStyle| | String| `width: 5%;height: 3px;background-color: rgba(255,255,255,.7);`| 当前项样式|
| defItemStyle| | String| `width: 3%;height: 3px;background-color: rgba(0,0,0,.7);`| 非当前项样式|
| itemStyle| | String| `margin: 0 .5%;`| 默认所有item的样式|