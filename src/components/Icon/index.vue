<template>
  <i class="iconfont icon-container" :class="fontClass"></i>
</template>

<script>
// 图标样式映射
const classMap = {
  home: "iconzhuye",
  success: "iconzhengque",
  error: "iconcuowu",
  close: "iconguanbi",
  warn: "iconjinggao",
  info: "iconxinxi",
  blog: "iconblog",
  code: "iconcode",
  about: "iconset_about_hov",
  weixin: "iconweixin",
  mail: "iconemail",
  github: "icongithub",
  qq: "iconsign_qq",
  arrowUp: "iconiconfonticonfonti2copy",
  arrowDown: "iconiconfonticonfonti2",
  empty: "iconempty",
  chat: "iconliuyan",
};

export const types = Object.keys(classMap);

export default {
  name: 'Icon',
  props: {
    type: { // 图标类型
      type: String,
      required: true
    }
  },
  computed: {
    fontClass() {
      return classMap[this.type];
    }
  }
}
</script>

<style scoped>
@import url('//at.alicdn.com/t/font_2164449_nalfgtq7il.css');

.iconfont {
  color: inherit;
  font-size: inherit;
}
</style>