<template>
  <h1>This is video Page</h1>
  <video
    src="../assets/videos/mov_hts-samp003.mp4"
    controls
    width="500"
  ></video>
  <div>
    <VideoPlayer src="../assets/videos/mov_hts-samp003.mp4" />
  </div>
</template>

<script>
import VideoPlayer from 'nuxt-video-player'
export default {
  layout: 'video',
  components: {
    VideoPlayer,
  },
  data() {
    return {
      videoPath: '../assets/videos/mov_hts-samp003.mp4',
    }
  },
}
</script>
