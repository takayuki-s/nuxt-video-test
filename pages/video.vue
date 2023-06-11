<template>
  <h1>This is video Page</h1>
  <video
    src="../assets/videos/mov_hts-samp003.mp4"
    controls
    width="500"
  ></video>
  <div>
    <div class="player-container">
      <vue-core-video-player :src="videoPath"></vue-core-video-player>
    </div>
  </div>
</template>

<script>
export default {
  layout: 'video',
  data() {
    return {
      videoPath: '../assets/videos/mov_hts-samp003.mp4',
    }
  },
}
</script>
