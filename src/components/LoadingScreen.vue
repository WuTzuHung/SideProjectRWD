<script setup>
import { ref, onMounted } from 'vue';

const isLoading = ref(true);
const loadProgress = ref(0);

// onMounted(() => {
//   // 模拟加载过程，可以用实际的资源加载逻辑替代
//   setTimeout(() => {
//     isLoading.value = false;
//   }, 3000); // 3秒后隐藏加载画面
// });
// 模擬資源加載進度
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
        <img src="/pictures/003.gif" alt="Loading GIF" class="loading-gif" />
      <p>Now Loading...</p>
    <div class="progress-bar">
      <div class="progress" :style="{ width: loadProgress + '%' }"></div>
    </div>
  </div>
</template>


<style scoped>
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