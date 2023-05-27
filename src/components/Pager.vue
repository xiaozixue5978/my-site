<template>
  <div class="pager-container">
    <a href="" class="disabled">|&lt;&lt;</a>
    <a href="">&lt;&lt;</a>
    <a href="">1</a>
    <a href="">2</a>
    <a href="">3</a>
    <a href="" class="active">4</a>
    <a href="">5</a>
    <a href="">6</a>
    <a href="">&gt;&gt;</a>
    <a href="">&gt;&gt;|</a>
  </div>
</template>

<script>
export default {
  name: 'Pager',
  props: {
    current: { // 当前页码
      type: Number,
      default: 1
    },
    total: { // 总数据
      type: Number,
      default: 0,
    },
    limit: { // 页容量
      type: Number,
      default: 10
    },
    visibleNumber: { // 可见页码数
      type: Number,
      default: 10
    }
  }
}
</script>

<style lang="less" scoped>
@import '~@/styles/var.less';

.pager-container {
  display: flex;
  justify-content: center;
  margin: 20px 0;

  a {
  color: @primary;
  margin: 0 6px;
  cursor: pointer;

  &.active {
    color: @words;
    cursor: text;
    font-weight: bold;
  }

  &.disabled {
    color: @lightWords;
    cursor: not-allowed;
  }
}
}
</style>