##### 1.9抽取回到顶部组件

因为之前的回到顶部组件 `backTop` 是直接放到 common 目录中，然后在 home 中引入，基本样式都是直接在home定制的。

这样并不好，所以我们需要先将 ` backTop`  组件放到项目相关的 content 目录中，在 content 中做基本的样式处理，再导入home组件或当前组件中使用。

###### MainBackTop：

```html
<template>
  <back-top class="back-top" :backTop="mainBackTop">
    <img src="~assets/img/home/arrow.svg" alt="" />
  </back-top>
</template>

<script>
import BackTop from "components/common/backTop/BackTop";
export default {
  name: "MainBackTop",
  props: {
    mainBackTop: {
      type: Object,
      default() {
        return {};
      },
    },
  },
  components: {
    BackTop,
  },
};
</script>

<style>
.back-top {
  width: 40px;
  height: 40px;
  position: fixed;
  bottom: 60px;
  right: 8px;
  z-index: 100;
  border-radius: 50%;
  background-color: rgba(255, 255, 255, 0.8);
}
.back-top img {
  height: 40px;
  width: 28px;
  margin: 0 auto;
  display: block;
}
</style>
```

###### 使用MainBackTop并传参：

```js
<main-back-top
  v-show="isShow"
  :main-back-top="{ el: 'XXX', move: XXX }"
/>
```