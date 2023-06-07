<template>
  <h1>This is video Page</h1>
  <video
    src="../assets/videos/mov_hts-samp003.mp4"
    controls
    width="500"
  ></video>
  <Vue3CanvasVideoPlayer
    :src="videoPath"
    :muted="true"
    :autoplay="true"
    :range="[10, 20]"
    :fps="30"
    :bbox="{
      data: {
        100: [0, 200, 100, 400],
        101: [10, 210, 110, 410],
        102: [20, 220, 120, 420],
      },
      borderSize: 1,
      borderColor: 'rgba(255, 0, 0, 0.5)',
      fillColor: 'rgba(0, 0, 255, 0.5)',
    }"
    :type="'contain'"
    :message-time="1000"
    :preview="true"
    :dark-mode="true"
  />
</template>

<script>
import Vue3CanvasVideoPlayer from 'vue3-canvas-video-player'
import 'vue3-canvas-video-player/dist/style.css'
export default {
  components: {
    Vue3CanvasVideoPlayer,
  },
  layout: 'video',
  data() {
    return {
      videoPath: '../assets/videos/mov_hts-samp003.mp4',
    }
  },
}
</script>
