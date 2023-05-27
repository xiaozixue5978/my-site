<template>
  <img class="avatar-container" :src="url" :style="{ width: size + 'px', height: size + 'px' }">
</template>

<script>
export default {
  name: 'Avatar',
  props: {
    url: { // 图片url
      type: String,
      required: true
    },
    size: { // 图片宽高
      type: Number,
      default: 50
    }
  }
}
</script>

<style scoped>
.avatar-container {
  border-radius: 50%;
  object-fit: cover;
}
</style>