<template>
  <view class='statusbar' :style="{ backgroundColor: color }"></view>
</template>

<script>
  export default {
    props: ['color']
  }
</script>

<style scoped>
  .statusbar {
    height: 23px;
  }
</style>