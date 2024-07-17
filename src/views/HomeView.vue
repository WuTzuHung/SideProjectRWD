<script setup>
import { ref } from 'vue';
import AudioButton from '../components/AudioButton.vue'; // 导入 AudioButton

const currentTab = ref('tab1');

const audioResourceList = ref([
    { id: 'sound1', src: '/sounds/TestSounds.mp3', volume: 1.0 },
    { id: 'sound2', src: '/sounds/Test2.mp3', volume: 1.0 },
    { id: 'sound3', src: '/sounds/a政經同學.mp3', volume: 1.0 },
    { id: 'sound4', src: '/sounds/你這個妹控.mp3', volume: 1.0 },
    { id: 'sound5', src: '/sounds/就是要親的才好.mp3', volume: 1.0 },
    { id: 'sound6', src: '/sounds/從床底抓腳.mp3', volume: 1.0 },
    { id: 'sound7', src: '/sounds/早安我的哥哥.mp3', volume: 1.0 },
    { id: 'sound8', src: '/sounds/為什麼因為會起反應嗎.mp3', volume: 1.0 },
    { id: 'sound9', src: '/sounds/男主久等了.mp3', volume: 1.0 },
    { id: 'sound10', src: '/sounds/真冷淡這時候要說久等了真是抱歉.mp3', volume: 1.0 },
    { id: 'sound11', src: '/sounds/起床撲擊給我高興點.mp3', volume: 1.0 },
    { id: 'sound12', src: '/sounds/恩久等了久等了.mp3', volume: 1.0 },


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
        <AudioButton soundId="sound3" label="あ、政近君来てくださったのですね" :audioResourceList="audioResourceList" />
        <AudioButton soundId="sound4" label="ただのDEAR VENUS？もうお兄ちゃんってば～シ、ス、コ、ン🤍" :audioResourceList="audioResourceList" />
        <AudioButton soundId="sound5" label="ばっか野郎！実の兄弟だからいいんじゃねえか！" :audioResourceList="audioResourceList" />
        <AudioButton soundId="sound6" label="もう～しょうがないな～じゃあ今度はベッドの下に潜り込んでおいて、降りる瞬間に足つかんであげるね" :audioResourceList="audioResourceList" />
        <AudioButton soundId="sound7" label="グッドモーニン～マイブラザー" :audioResourceList="audioResourceList" />
        <AudioButton soundId="sound8" label="なんで？反応しちゃうからｗ？" :audioResourceList="audioResourceList" />
        <AudioButton soundId="sound9" label="待ったーごめん～" :audioResourceList="audioResourceList" />
        <AudioButton soundId="sound10" label="つれないですね、そこは待ったごめん～とおしゃってくださいな" :audioResourceList="audioResourceList" />
        <AudioButton soundId="sound11" label="おいおい可愛い妹のボディプレスじゃねえか、喜べよ" :audioResourceList="audioResourceList" />
        <AudioButton soundId="sound12" label="うん！待った待ったｗ" :audioResourceList="audioResourceList" />
        

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