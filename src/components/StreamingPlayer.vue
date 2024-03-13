<script setup>
import HLSPlayer from './HLSPlayer.vue'
import RTMPPlayer from './RTMPPlayer.vue'
defineProps({
  type: String,
  url: String,
})
</script>

<template>
  <HLSPlayer :url="url" v-if="type === 'HLS'"/>
  <RTMPPlayer :url="url" v-else-if="type === 'RTMP'"/>
  <p v-else>TYPE ERROR</p>
</template>

<style scoped>
</style>
