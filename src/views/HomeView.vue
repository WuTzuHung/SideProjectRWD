<script setup>
import { ref, provide } from 'vue';
import AudioButton from '../components/AudioButton.vue'; 
import LoadingScreen from '../components/LoadingScreen.vue';

const isLoading = ref(true);
const loadProgress = ref(0);

// 當前播放的音頻
const currentAudio = ref(null);

// 停止當前音頻
const stopCurrentAudio = () => {
  if (currentAudio.value) {
    currentAudio.value.pause();
    currentAudio.value.currentTime = 0;
    currentAudio.value = null;
  }
};

// 提供全局的音頻管理器
provide('audioManager', {
  currentAudio,
  stopCurrentAudio
});

// 供按鈕使用的停止所有音頻的方法
const stopAllAudio = () => {
  stopCurrentAudio();  // 直接調用 stopCurrentAudio 方法
};


const currentTab = ref('tab1');

const audioResourceList = ref([
    { id: 'amasachikakun', src: '/sounds/amasachikakun.mp3', volume: 1.0 },
    { id: 'tadanodearvenus', src: '/sounds/tadanodearvenus.mp3', volume: 1.0 },
    { id: 'baxtukayarou', src: '/sounds/baxtukayarou.mp3', volume: 1.0 },
    { id: 'mousyouganaina', src: '/sounds/mousyouganaina.mp3', volume: 1.0 },
    { id: 'guxtutomo-nin', src: '/sounds/guxtutomo-nin.mp3', volume: 1.0 },
    { id: 'nandehannou', src: '/sounds/nandehannou.mp3', volume: 1.0 },
    { id: 'maxtuta-gomen', src: '/sounds/maxtuta-gomen.mp3', volume: 1.0 },
    { id: 'tsurenaidesune', src: '/sounds/tsurenaidesune.mp3', volume: 1.0 },
    { id: 'oioikawaii', src: '/sounds/oioikawaii.mp3', volume: 1.0 },
    { id: 'unmaxtutamaxtuta', src: '/sounds/unmaxtutamaxtuta.mp3', volume: 1.0 },

]);
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
  <LoadingScreen v-if="isLoading" />
  <div v-else>
  <div class="tabs">
    <button
        class="tabsButton"
        :class="{ active: currentTab === 'tab1' }"
        @click="currentTab = 'tab1'"
      >
        第2話
      </button>
      <button
        class="tabsButton"
        :class="{ active: currentTab === 'tab2' }"
        @click="currentTab = 'tab2'"
      >
        第3話
      </button>
      <button
        class="tabsButton"
        :class="{ active: currentTab === 'tab3' }"
        @click="currentTab = 'tab3'"
      >
        第4話
      </button>
      <button
        class="tabsButton"
        :class="{ active: currentTab === 'tab4' }"
        @click="currentTab = 'tab4'"
      >
        第5話
      </button>
    </div>
  <!-- <div class="Container"> -->
    <div class="currentTabContainer">
      <div 
      v-if="currentTab === 'tab1'" 
      class="tab-content tab1"
      :class="{ 'no-top-border': currentTab === 'tab1' }"
    >
        <h1 class="suouyikiButton">周防有希ボタン2</h1>
        <AudioButton soundId="amasachikakun" label="あ、政近君 来てくださったのですね" :audioResourceList="audioResourceList" />
        <AudioButton soundId="tadanodearvenus" label="ただのディア・ビーナス？も～お兄ちゃんってば～ シ・ス・コ・ン🤍" :audioResourceList="audioResourceList" />
        <AudioButton soundId="baxtukayarou" label="ばっか野郎！実の兄弟だからいいんじゃねえか！" :audioResourceList="audioResourceList" />
        <AudioButton soundId="mousyouganaina" label="むぅ… しょ～がないなあ～じゃあ今度はベッドの下に潜り込んでおいて、降りた瞬間に足掴んであげるね？" :audioResourceList="audioResourceList" />
        <AudioButton soundId="guxtutomo-nin" label="グッドモーニ～ン、マイブラザ～" :audioResourceList="audioResourceList" />
        <AudioButton soundId="nandehannou" label="なんで？ 反応しちゃうからｗ？" :audioResourceList="audioResourceList" />
        <AudioButton soundId="maxtuta-gomen" label="まったぁ？ごめぇ〜ん" :audioResourceList="audioResourceList" />
        <AudioButton soundId="tsurenaidesune" label="つれないですね、そこは『待った？ ごめぇ〜ん』とおしゃってくださいな" :audioResourceList="audioResourceList" />
        <AudioButton soundId="oioikawaii" label="おいおい 可愛い妹による寝起きボディープレスじゃねえか、喜べよ" :audioResourceList="audioResourceList" />
        <AudioButton soundId="unmaxtutamaxtuta" label="うん！ 待った待った～♪" :audioResourceList="audioResourceList" />
        

      </div>
      <div 
      v-if="currentTab === 'tab2'" 
      class="tab-content tab2"
      :class="{ 'no-top-border': currentTab === 'tab2' }"
    >
        <h1 class="suouyikiButton">周防有希ボタン3</h1>
        
      </div>
      <div 
      v-if="currentTab === 'tab3'" 
      class="tab-content tab3"
      :class="{ 'no-top-border': currentTab === 'tab3' }"
    >
        <h1 class="suouyikiButton">周防有希ボタン4</h1>

      </div>
      <div 
      v-if="currentTab === 'tab4'" 
      class="tab-content tab4"
      :class="{ 'no-top-border': currentTab === 'tab4' }"
    >
        <h1 class="suouyikiButton">周防有希ボタン5</h1>

      </div>
    </div>
    <button class="stop" @click="stopAllAudio">ストップ</button>
    <img src="/pictures/001.png" alt="" class="pic01">
  <!-- </div> -->
</div>
</template>

<style>

body {
  /* font-family: 'Noto Sans JP', sans-serif; */
  background-color: rgba(182, 180, 177, 0.25);
}

.suouyikiButton{
  font-family: 'Noto Sans JP', sans-serif;
}

 .stop {
  position: fixed;
  bottom:2dvh;
  right: 0%;
  z-index: 1000;
  padding: 5px 10px;
  margin: 5px 10px 15px;
  font-size: 13px;
  cursor: pointer;
  border-radius: 10px;
  border-width: 0px;
  background-color: rgb(51, 204, 153); 
  color: white;
  font-family: 'Noto Sans JP', sans-serif;
  box-shadow: 0 9px rgb(34, 142, 99); 
}

.stop:hover {background-color: #36b68d}

.stop:active {
  background-color: #36b68d;
  box-shadow: 0 5px rgb(34, 142, 99);
  transform: translateY(4px);
} 

.tabs{
  width: 80%;
  margin-top: 7dvh;
  margin-left: 10%;
  display: flex;
  justify-content: space-around;
}

.tabsButton{
  cursor: pointer;
  font-size: 13pt;
  font-family: 'Noto Sans JP', sans-serif;
  background-color: pink;
  border: 1px solid pink;
  border-bottom: none;
  border-top-left-radius: 10px; 
  border-top-right-radius: 10px; 
}

.tabsButton.active{
  background-color: white;
}

  .currentTabContainer{
    display: flex; /* 使用 Flexbox */
    justify-content: center; /* 左右对齐 */
    
    
  }

  .tab-content {
    box-sizing: border-box; /* 包含內邊距與邊框 */
    width: 90%;
    min-height: 60dvh;
    padding: 0.1px;
    margin: 0%;
  border: 1px solid pink;
  border-radius: 10px;

  /* border: 1px solid #121111;  */
  /* border-radius: 8px;  */
  /* margin-top: 10px;  */
}

.tab-content.no-top-border {
  border-top: none; /* 移除上邊框 */
}

.pic01{
    max-width: 90%; /* 限制最大寬度 */
    min-height: 10dvh;    /* 自動調整高度 */
  }

.tab1 {
  background-color: white; 

  
}

.tab2 {
  background-color: white; 
}

.tab3 {
  background-color: white;
}

.tab4 {
  background-color: white;
}

/* } */



/* iPad: 768 - 1199px */
@media (min-width: 768px) {
    .Container{
  background-color:yellow;
}
}

/* PC: 1200px 以上 */
@media (min-width: 1200px) {
    .Container {
        background-color: red; 
    }

    .tabs{
      margin-top: 20dvh;
    }

    .tabsButton{
      font-size: 15pt;
      width: 18%;
      height: 6dvh;
    }

    .tab-content{
      min-height: 50dvh;
  }

    .pic01{
    max-width: 40%; /* 限制最大寬度 */
    min-height: 40dvh;    /* 自動調整高度 */
  }

  .stop{
  bottom:3dvh;
  right: 3%;
  padding: 10px 20px;
  font-size: 16px;

  }

  
}

</style>