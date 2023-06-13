<template>
  <h1>This is video Page</h1>
  <div class="file-input">
    <!-- ファイル入力 -->
    <input type="file" accept="video/mp4" @change="fileSelect" />
    <!-- プレビューとして表示 -->
    <video controls ref="previewVideo">
      <source :src="src" type="video/mp4" />
    </video>
  </div>
</template>

<script setup>
import { ref } from 'vue'
const src = ref()
const previewVideo = ref()

// ファイル選択
const fileSelect = async (e) => {
  console.log('ファイルチェンジ！', e)
  const file = e.target.files[0]
  if (!file || !file.type.match('video/*')) {
    return
  }
  // 選択された動画を見えるようにする。
  src.value = URL.createObjectURL(file)
  console.log('src!', src.value)
  // ロードする
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
