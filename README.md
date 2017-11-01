# ReactNative-Android-Attention
### 记录ReactNative Android平台上 一些需要注意的特性

* width，height ，lineHeight不能出现小数点，不然会报错
* position的节点，设置zIndex后，如果didMount后有重新渲染，可能会导致节点渲染不出来的问题；
  解决方案不设置zIndex，和调整节点顺序可以避免
* 金钱符号 + 价格， 可能会导致某些机型渲染有问题，解决方法，字体不加粗
* <View style={{  overflow: 'hidden',marginTop: 64}}></View> 
  设置了overflow hidden的元素，如果同级元素设置了position, 例如动画使2个View在界面同一区域里，overflow:hidden 失效
  解决方法，设置一个backgroundColor: 'transparent'
