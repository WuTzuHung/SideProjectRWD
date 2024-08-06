<script setup>
import { ref } from 'vue';
import AudioButton from '../components/AudioButton.vue'; // 导入 AudioButton
import LoadingScreen from '../components/LoadingScreen.vue';

const isLoading = ref(true);
const loadProgress = ref(0);


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
      <button @click="currentTab = 'tab1'">Tab 1</button>
      <button @click="currentTab = 'tab2'">Tab 2</button>
      <button @click="currentTab = 'tab3'">Tab 3</button>
      <button @click="currentTab = 'tab4'">Tab 4</button>
    </div>
  <!-- <div class="Container"> -->
    <div class="currentTabContainer">
    <div v-if="currentTab === 'tab1'" class="tab-content tab1">
        <h1>周防有希ボタン</h1>
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
      <div v-if="currentTab === 'tab2'" class="tab-content tab2">
        <h2>Tab 2 Content</h2>
        
      </div>
      <div v-if="currentTab === 'tab3'" class="tab-content tab3">
        <h2>Tab 3 Content</h2>

      </div>
      <div v-if="currentTab === 'tab4'" class="tab-content tab4">
        <h2>Tab 4 Content</h2>

      </div>
    </div>
    <img src="/pictures/001.png" alt="" class="pic01">
  <!-- </div> -->
</div>
</template>

<style>

body {
  font-family: 'Noto Sans JP', sans-serif;
  background-color: rgba(182, 180, 177, 0.25);
}

/* .Head1{
  width: 100%;
  height: 15dvh;
  background-color: blueviolet;
} */

/* .Container{
  width: 100%;
  height: 85dvh;
  background-color: purple; */

  /* .button{
    height: 5dvh;
  } */

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
  border-radius: 10PX;

  /* border: 1px solid #121111;  */
  /* border-radius: 8px;  */
  /* margin-top: 10px;  */
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

    .tab-content{
      min-height: 50dvh;
  }

    .pic01{
    max-width: 40%; /* 限制最大寬度 */
    min-height: 40dvh;    /* 自動調整高度 */
  }

  
}

</style>