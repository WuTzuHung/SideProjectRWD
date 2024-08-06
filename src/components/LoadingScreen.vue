<script setup>
import { ref } from 'vue';
import AudioButton from '../components/AudioButton.vue'; // 导入 AudioButton


const isLoading = ref(true);
const loadProgress = ref(0);

const audioResourceList = ref([
    { id: 'unmaxtutamaxtuta', src: '/sounds/unmaxtutamaxtuta.mp3', volume: 1.0 },

]);

const simulateLoading = () => {
  let progress = 0;
  const interval = setInterval(() => {
    progress += Math.random() * 10;
    if (progress >= 100) {
      clearInterval(interval);
      isLoading.value = false;
    }
    loadProgress.value = progress;
  }, 300); // 模擬每300毫秒更新一次進度
};

// 模擬資源加載
simulateLoading();
</script>

<template>
    <div class="loading-screen" v-if="isLoading">
        <img src="/pictures/004.gif" alt="Loading GIF" class="loading-gif" />
        <AudioButton soundId="unmaxtutamaxtuta" label="うん！ 待った待った～♪" :audioResourceList="audioResourceList" />
      <p>Now Loading...</p>
    <div class="progress-bar">
      <div class="progress" :style="{ width: loadProgress + '%' }"></div>
    </div>
  </div>
</template>


<style scoped>

body {
  font-family: 'Noto Sans JP', sans-serif;
}

.loading-screen {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}



.progress-bar {
  width: 200px;
  height: 17px;
  border: solid 1px #ffffff;
  border-radius: 4px;
  overflow: hidden;
}

.progress {
  height: 100%;
  background-color: rgb(255, 160, 160);
  transition: width 0.3s ease; /* 使用過渡效果使進度條平滑變化 */
}

.loading-gif{
    /* watch:30%; */
    height: 30dvh;
    margin-bottom: 2dvh;
}

p {
    font-weight:bold;
    font-size: 25px;
    color: #FFFFFF;
}


/* PC: 1300px 以上 */
@media (min-width: 1200px) {

    .progress-bar {
  width: 300px;
  height: 20px;
  border: solid 1px #ffffff;
  border-radius: 4px;
  overflow: hidden;
}

    .loading-gif{
    height: 50dvh;
}

p {
    font-weight:bold;
    font-size: 35px;
    color: #FFFFFF;
}

  
}
</style>