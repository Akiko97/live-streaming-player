<script setup>
import { onMounted, onBeforeUnmount, ref } from 'vue'
import Hls from 'hls.js'
const url = '/api/live/test/test.m3u8?token=123'
const videoElement = ref(null)
let hls = null
onMounted(() => {
  if (Hls.isSupported()) {
    hls = new Hls()
    hls.loadSource(url)
    hls.attachMedia(videoElement.value)
  } else if (videoElement.value.canPlayType('application/vnd.apple.mpegurl')) {
    videoElement.value.src = url
  }
})
onBeforeUnmount(() => {
  if (hls) {
    hls.destroy()
  }
})
</script>

<template>
  <div>
    <video ref="videoElement" controls style="width: 100%;"></video>
  </div>
</template>

<style scoped>
</style>
