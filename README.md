# ReactNative-Android-Attention
### 记录ReactNative Android平台上 一些需要注意的特性

* width，height 不能出现小数点，不然会报错
* position的节点，设置zIndex后，如果didMount后有重新渲染，可能会导致节点渲染不出来的问题
* 金钱符号 + 价格， 可能会导致某些机型渲染有问题，解决方法，字体不加粗
