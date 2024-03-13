<script setup>
const props = defineProps({
  url: String,
})
import flvjs from 'flv.js'
import { onMounted, onBeforeUnmount, ref } from 'vue'
const videoElement = ref(null)
let flvPlayer = null
const createPlayer = () => {
  if (flvjs.isSupported()) {
    flvPlayer = flvjs.createPlayer({
      type: 'flv',
      url: props.url,
    })
    flvPlayer.attachMediaElement(videoElement.value)
    flvPlayer.load()
    flvPlayer.play()
  }
}
onMounted(() => {
  createPlayer()
})
onBeforeUnmount(() => {
  if (flvPlayer) {
    flvPlayer.destroy()
  }
})
</script>

<template>
  <h1>RTMP</h1>
  <div>
    <video ref="videoElement" controls style="width: 100%;"></video>
  </div>
</template>

<style scoped>

</style>
