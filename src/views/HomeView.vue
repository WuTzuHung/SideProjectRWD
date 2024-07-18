<script setup>
import { ref } from 'vue';
import AudioButton from '../components/AudioButton.vue'; // 导入 AudioButton

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
</script>



<template>
  <div class="tabs">
      <button @click="currentTab = 'tab1'">Tab 1</button>
      <button @click="currentTab = 'tab2'">Tab 2</button>
      <button @click="currentTab = 'tab3'">Tab 3</button>
      <button @click="currentTab = 'tab4'">Tab 4</button>
    </div>
  <!-- <div class="Container"> -->
    <div class="currentTabContainer">
    <div v-if="currentTab === 'tab1'" class="tab-content tab1">
        <h2>周防有希</h2>
        <AudioButton soundId="amasachikakun" label="あ、政近君 来てくださったのですね" :audioResourceList="audioResourceList" />
        <AudioButton soundId="tadanodearvenus" label="ただのDEAR VENUS？もうお兄ちゃんってば～ シ、ス、コ、ン🤍" :audioResourceList="audioResourceList" />
        <AudioButton soundId="baxtukayarou" label="ばっか野郎！実の兄弟だからいいんじゃねえか！" :audioResourceList="audioResourceList" />
        <AudioButton soundId="mousyouganaina" label="もう しょうがないな～じゃあ今度はベッドの下に潜り込んでおいて、降りる瞬間に足つかんであげるね" :audioResourceList="audioResourceList" />
        <AudioButton soundId="guxtutomo-nin" label="グッドモーニン～マイブラザー" :audioResourceList="audioResourceList" />
        <AudioButton soundId="nandehannou" label="なんで？ 反応しちゃうからｗ？" :audioResourceList="audioResourceList" />
        <AudioButton soundId="maxtuta-gomen" label="待ったーごめん～" :audioResourceList="audioResourceList" />
        <AudioButton soundId="tsurenaidesune" label="つれないですね、そこは『待った ごめん～』とおしゃってくださいな" :audioResourceList="audioResourceList" />
        <AudioButton soundId="oioikawaii" label="おいおい可愛い妹による寝起きボディプレスじゃねえか、喜べよ" :audioResourceList="audioResourceList" />
        <AudioButton soundId="unmaxtutamaxtuta" label="うん、待った 待った～" :audioResourceList="audioResourceList" />
        

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

</template>

<style>

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
    width: 80%;
    min-height: 60dvh;
    padding: 0.1px;
    margin: 0%;
  /* border: 1px solid #121111;  */
  /* border-radius: 8px;  */
  /* margin-top: 10px;  */
}

.pic01{
    max-width: 80%; /* 限制最大寬度 */
    min-height: 30dvh;    /* 自動調整高度 */
  }

.tab1 {
  background-color: #8cea18; 

  
}

.tab2 {
  background-color: #09bcd3; 
}

.tab3 {
  background-color: #ea960d; 
}

.tab4 {
  background-color: #99129e; 
}

/* } */



/* iPad: 576px - 767px */
@media (min-width: 768px) {
    .Container{
  background-color:yellow;
}
}

/* PC: 1300px 以上 */
@media (min-width: 1200px) {
    .Container {
        background-color: red; 
    }

    .tab-content{
      min-height: 50dvh;
  }

    .pic01{
    max-width: 40%; /* 限制最大寬度 */
    min-height: 50dvh;    /* 自動調整高度 */
  }

  
}

</style>