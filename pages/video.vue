<template>
  <NuxtLayout>
    <h1>This is video Page</h1>
    <div class="file-input">
      <input
        id="file-input"
        type="file"
        accept="video/mp4"
        @change="fileSelect"
      />
      <div class="error">{{ errorMessage }}</div>
      <video
        controls
        preload="none"
        ref="previewVideo"
        @loadedmetadata="checkDuration"
      >
        <source :src="src" type="video/mp4" />
      </video>
    </div>
  </NuxtLayout>
</template>

<script setup>
import { ref } from 'vue'
const src = ref(null)
const previewVideo = ref(null)
const errorMessage = ref('')
const MIN_DURATION = 10
const MAX_DURATION = 60
const MAX_SIZE = 4000000

const fileSelect = async (e) => {
  const file = e.target.files[0]
  if (!file || !file.type.match('video/*')) {
    errorMessage.value = 'ファイル形式が間違っています'
    clearFile()
    return
  }

  if (file.size > MAX_SIZE) {
    errorMessage.value = 'ファイルサイズが大きすぎます'
    clearFile()
    return
  }
  src.value = URL.createObjectURL(file)
  previewVideo.value.load()
}
const checkDuration = () => {
  if (previewVideo.value.duration > MAX_DURATION) {
    errorMessage.value = '再生時間が長すぎます'
    clearFile()
  }
  if (previewVideo.value.duration < MIN_DURATION) {
    errorMessage.value = '再生時間が短すぎます'
    clearFile()
  }
}
const clearFile = () => {
  const video = document.getElementById('file-input')
  video.value = null
  src.value = null
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
.error {
  color: #ff0000;
}
</style>
