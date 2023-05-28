<template>
  <div>
    <Avatar url="https://t15.baidu.com/it/u=1372841570,3864405121&fm=58&s=DE913BC3663335941B0484C80300E0D1" :size="200" />
    <Icon type="success" />
    <Pager :total="total" :current="current" @pageChange="handlePageChange" :visibleNumber="20" />
  </div>
</template>

<script> 
import Avatar from '@/components/Avatar';
import Icon from '@/components/Icon';
import Pager from '@/components/Pager';

export default {
  name: 'App',
  components: {
    Avatar,
    Icon,
    Pager
  },
  data() {
    return {
      total: 205,
      current: 10
    }
  },
  methods: {
    handlePageChange(newPage) {
      this.current = newPage;
    }
  }
}
</script>

<style scoped>
.iconfont {
  font-size: 28px;
  color: #f40;
}
</style>