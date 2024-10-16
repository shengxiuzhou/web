<template>
  <el-row class="body-container">
    <Gallary></Gallary>
    <Partner></Partner>
  </el-row>
</template>

<script setup>
import Gallary from './Gallary.vue'
import Partner from './Partner.vue'
</script>
<style scoped>
  .body-container {
    background:#f8faff;
  }
</style>