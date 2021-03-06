# ReactNative-Android-Attention
### 记录ReactNative Android平台上 一些需要注意的特性

* width，height ，lineHeight不能出现小数点，不然会报错
* position的节点，设置zIndex后，如果didMount后有重新渲染，可能会导致节点渲染不出来的问题；
  解决方案不设置zIndex，和调整节点顺序可以避免
* 金钱符号 + 价格， 可能会导致某些机型渲染有问题，解决方法，字体不加粗
* <View style={{  overflow: 'hidden',marginTop: 64}}></View> 
  设置了overflow hidden的元素，如果同级元素设置了position, 例如动画使2个View在界面同一区域里，overflow:hidden 失效
  解决方法，设置一个backgroundColor: 'transparent'
* 代码里如果使用了 ref，this.refs.$ref ，push跳转切换页面时候可能会卡顿百来毫秒、甚至数百毫秒
* 背景渐变方法 不适宜使用代码渲染实现，android大量的渲染计算会造成页面卡顿，界面即使看不见变化，代码可能存在不停渲染
* 使用LayoutAnimation 需要设置这行代码开启； 
  if (Platform.OS === 'android') {
	  UIManager.setLayoutAnimationEnabledExperimental(true)
  }
  另外LayoutAnimation.configureNext(config: Config, onAnimationDidEnd?: Function)， 
  ios有动画结束callback，android需要自己用 setTimeout之类模拟
* JSON.stringify('{}') android平台上是 'null' 而不是 '{}'
* Android Modal会自带一个onRequestClose 属性，而且是必传的，不然浮层关闭会触发这个事件就会导致error，详情参考
  https://kylewbanks.com/blog/why-react-native-modals-require-onrequestclose-callback-property-on-android
* Android真机下 import {cloneDeep} from 'lodash' ，cloneDeep如果深度拷贝一个例如1M的数据， 会存在性能问题，可能需要4s~ 5s;取代方法 可以先     JSON.parse(JSON.stringify(obj))
* Android, Text标签设置opacity 如果带color属性，设置好像没有生效，(|变淡)验证代码：<Text key={i}><Text style={{ color: '#f3cc99', opacity: 0.2 }}>{' | '}</Text><Text>{item}</Text></Text>， 如果有类似需求，可以设置一个淡一点的颜色来代替。
