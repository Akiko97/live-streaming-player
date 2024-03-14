<script setup>
import StreamingPlayer from './components/StreamingPlayer.vue'
import { ref } from 'vue'
const watermark = ref(['LSS', '***.***.***.***'])
</script>

<template>
  <el-watermark font="rgba(0, 0, 0, .15)" :content="watermark">
    <el-container>
      <el-header>
        <div class="header-container">
          <div class="header-title">
            <el-text type="primary" size="large" tag="b">Live Streaming</el-text>
            <el-text type="warning" size="small" tag="sup">Secret</el-text>
          </div>
        </div>
      </el-header>
      <el-main>
        <StreamingPlayer/>
      </el-main>
    </el-container>
  </el-watermark>
</template>

<style scoped>
.header-container {
  display: flex;
  height: 100%;
  box-shadow: var(--el-box-shadow-light);
  align-items: center;
  justify-content: center;
}
</style>
