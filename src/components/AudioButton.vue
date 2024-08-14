<script setup>
import { inject, ref } from 'vue';

const props = defineProps({
  soundId: {
    type: String,
    required: true
  },
  label: {
    type: String,
    required: true
  },
  audioResourceList: {
    type: Array,
    required: true
  }
});

// 注入全域音效管理器
const audioManager = inject('audioManager');
const isPlaying = ref(false);

const playAudio = () => {
  const audioResource = props.audioResourceList.find(resource => resource.id === props.soundId);
  if (audioResource) {
    if (audioManager.currentAudio.value) {
      // 檢查當前播放的音效是否與新的音效相同
      if (audioManager.currentAudio.value.src !== audioResource.src) {
        audioManager.stopCurrentAudio(); // 如果不同，停止目前播放的音效
      } else {
        // 如果相同，重新開始播放音效
        audioManager.currentAudio.value.currentTime = 0; // 重置到開始
        audioManager.currentAudio.value.play(); // 再次播放
        return; // 退出 playAudio，避免創建新的 Audio 實例
      }
    }

    // 創建新的 Audio 實例
    const newAudio = new Audio(audioResource.src);
    newAudio.volume = audioResource.volume;

    // 更新全域音效管理器
    audioManager.currentAudio.value = newAudio;

    newAudio.play();
    isPlaying.value = true;

    newAudio.addEventListener('ended', () => {
      isPlaying.value = false;
    });
  }
};

const handleButtonClick = () => {
  if (isPlaying.value && audioManager.currentAudio.value && audioManager.currentAudio.value.src === props.audioResourceList.find(resource => resource.id === props.soundId).src) {
    // 如果相同的音效已經在播放，重置並再次播放
    audioManager.currentAudio.value.currentTime = 0; // 重置到開始
    audioManager.currentAudio.value.play(); // 再次播放
  } else {
    // 如果沒有播放或不同的音效，播放新的音效
    playAudio();
  }
};
</script>

<template>
  <button class="button" @click="handleButtonClick">{{ label }}</button>
</template>

<style scoped>

button {
  padding: 10px 20px;
  margin: 5px 10px 15px;
  font-size: 16px;
  cursor: pointer;
  border-radius: 10px;
  border-width: 0px;
  background-color: rgb(245, 97, 122);
  color: white;
  font-family: 'Noto Sans JP', sans-serif;
  box-shadow: 0 9px #bd4646;
}

.button:hover {background-color: rgb(244, 70, 99)}

.button:active {
  background-color: rgb(244, 70, 99);
  box-shadow: 0 5px #bd4646;
  transform: translateY(4px);
}

</style>