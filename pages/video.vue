<template>
  <h1>This is video Page</h1>
  <div class="file-input">
    <input type="file" accept="video/mp4" @change="fileSelect" />
    <video controls ref="previewVideo">
      <source :src="src" type="video/mp4" />
    </video>
  </div>
</template>

<script setup>
import { ref } from 'vue'
const src = ref()
const previewVideo = ref()

const fileSelect = async (e) => {
  const file = e.target.files[0]
  if (!file || !file.type.match('video/*')) {
    return
  }
  src.value = URL.createObjectURL(file)
  previewVideo.value.load()
}
</script>

<style>
.file-input {
  width: 1000px;
  display: flex;
  flex-direction: column;
  gap: 10px;
}
</style>
