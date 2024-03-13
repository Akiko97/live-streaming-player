<script setup>
import StreamingPlayer from './components/StreamingPlayer.vue'
import { ref } from 'vue'
const watermark = ref(['LSS', '***.***.***.***'])
const type = ref('RTMP')
const url = ref('')
const urls = ref([
  {value: 'rtmp://'},
  {value: 'http://'},
])
const querySearch = (queryString, cb) => {
  const results = queryString
      ? urls.value.filter(createFilter(queryString))
      : urls.value
  cb(results)
}
const createFilter = (queryString) => {
  return (url) => {
    return (
        url.value.toLowerCase().indexOf(queryString.toLowerCase()) === 0
    )
  }
}
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
        <el-radio-group v-model="type" class="ml-4">
          <el-radio value="RTMP" size="large">RTMP</el-radio>
          <el-radio value="HLS" size="large">HLS</el-radio>
          <el-autocomplete
              v-model="url"
              :fetch-suggestions="querySearch"
              clearable
              placeholder="Please Input URL"
          />
        </el-radio-group>
        <StreamingPlayer :type="type" :url="url"/>
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
