<template>
  <view class="header">
    <text class="title">{{title}}</text>
  </view>
</template>

<script>
  export default {
    props: ['title']
  }
</script>

<style scoped>
  .header {
    color: white;
    background-color: #000;
    padding: 20px;
  }

  .title {
    font-size: 20px;
    font-weight: bold;
    color: white
  }
</style>