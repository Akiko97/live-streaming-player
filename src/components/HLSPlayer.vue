<script setup>
import { onMounted, onBeforeUnmount, ref } from 'vue'
import Hls from 'hls.js'
const props = defineProps({
  url: String,
})
const videoElement = ref(null)
let hls = null
onMounted(() => {
  if (Hls.isSupported()) {
    hls = new Hls()
    hls.loadSource(props.url)
    hls.attachMedia(videoElement.value)
  } else if (videoElement.value.canPlayType('application/vnd.apple.mpegurl')) {
    videoElement.value.src = props.url
  }
})
onBeforeUnmount(() => {
  if (hls) {
    hls.destroy()
  }
})
</script>

<template>
  <h1>HLS</h1>
  <div>
    <video ref="videoElement" controls style="width: 100%;"></video>
  </div>
</template>

<style scoped>

</style>
