<template>
  <div class="pager-container" v-if="pageNumber > 1">
    <a @click="handlePageChange(1)" :class="{ disabled: current === 1 }">|&lt;&lt;</a>
    <a @click="handlePageChange(current - 1)" :class="{ disabled: current === 1 }">&lt;&lt;</a>
    <a @click="handlePageChange(num)" v-for="(num,i) in numbers" :key="i" :class="{ active: num === current }">{{ num }}</a>
    <a @click="handlePageChange(current + 1)" :class="{ disabled: current === pageNumber }">&gt;&gt;</a>
    <a @click="handlePageChange(pageNumber)" :class="{ disabled: current === pageNumber }">&gt;&gt;|</a>
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
  },
  computed: {
    // 总页数
    pageNumber() {
      return Math.ceil(this.total / this.limit);
    },
    // 计算出最小可视数字
    visibleMin() {
      let min = this.current - Math.floor(this.visibleNumber / 2);
      if (min < 1) {
        min = 1;
      }
      return min;
    },
    // 计算出最大可视数字
    visibleMax() {
      let max = this.visibleMin + this.visibleNumber - 1;
      if (max > this.pageNumber) {
        max = this.pageNumber;
      }
      return max;
    },
    // 计算出最终在页面展示的数字
    numbers() {
      console.log(this.pageNumber);
      const nums = [];
      for (let i = this.visibleMin; i <= this.visibleMax; i++) {
        nums.push(i);
      }
      return nums;
    }
  },
  methods: {
    handlePageChange(newPage) {
      // 判断是否为第一页或最后一页
      if (newPage < 1 || newPage > this.pageNumber) {
        return;
      }
      // 判断newPage是否是当前页
      if (newPage === this.current) {
        return;
      }
      this.$emit('pageChange', newPage);
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