<script setup>
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <el-container>
    <el-header>
      <div class="header-container">
        <el-text type="primary" size="large" tag="b">Live Streaming</el-text>
        <el-text type="warning" size="small" tag="sup">Secret</el-text>
      </div>
    </el-header>
    <el-main>
      <HelloWorld msg="Vite + Vue" />
    </el-main>
  </el-container>
</template>

<style scoped>
.header-container {
  height: 100%;
  box-shadow: var(--el-box-shadow-light);
}
</style>
