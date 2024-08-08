<script setup>
import { ref, watch } from 'vue';

// 定义props
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
// 定义一个ref来保存当前音频实例
const currentAudio = ref(null);
const audioDuration = ref(0); // 存储音频时长
const isPlaying = ref(false); // 当前音频播放状态

const playAudio = () => {
  const audioResource = props.audioResourceList.find(resource => resource.id === props.soundId);
  if (audioResource) {
    // 如果当前有音频在播放，先停止它
    if (currentAudio.value) {
      currentAudio.value.pause();
      currentAudio.value.currentTime = 0; // 重置音频
    }

    currentAudio.value = new Audio(audioResource.src);
    currentAudio.value.volume = audioResource.volume;

    // 检查音频时长
    currentAudio.value.addEventListener('loadedmetadata', () => {
      audioDuration.value = currentAudio.value.duration; // 更新音频时长
      if (audioDuration.value <= 10) {
        // 10秒以下的音频自动播放
        currentAudio.value.play();
        isPlaying.value = true; // 更新播放状态
      }
    });

    // 播放音频
    currentAudio.value.play(); // 确保在加载元数据之前先调用play
    isPlaying.value = true; // 更新播放状态
  }
};

const handleButtonClick = () => {
  if (currentAudio.value) {
    if (audioDuration.value > 10) {
      // 如果音频时长超过10秒，点击时仅暂停
      if (isPlaying.value) {
        currentAudio.value.pause(); // 暂停音频
        currentAudio.value.currentTime = 0; // 重置音频
      } else {
        currentAudio.value.play(); // 播放音频
      }
      isPlaying.value = !isPlaying.value; // 切换播放状态
    } else {
      // 否则，调用playAudio
      playAudio();
    }
  } else {
    // 如果没有音频在播放，直接播放音频
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
  /* border: 1px solid black;
  border-right-width: 4px; 
  border-bottom-width: 4px; 
  border-left-width: 0px; 
  border-top-width: 0px;  */
  border-width: 0px;
  background-color: rgb(245, 97, 122);
  color: white;
  font-family: 'Noto Sans JP', sans-serif;
  box-shadow: 0 9px rgba(139, 0, 0, 0.4);
}

.button:hover {background-color: rgb(244, 70, 99)}

.button:active {
  background-color: rgb(244, 70, 99);
  box-shadow: 0 5px #bd4646;
  transform: translateY(4px);
}

</style>