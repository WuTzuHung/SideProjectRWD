<script>
import { ref } from 'vue';
import AudioButton from '../components/AudioButton.vue'; // 导入 AudioButton
const currentTab = ref('tab1');

export default {
  name: 'MyComponent', // 组件的名称
  setup() {
    return {
      currentTab,
    };
  },
  data() {
    return {
     
    };
  },
  methods: {
    
  },
  computed: {
    // 计算属性
    
  },
  mounted() {
    // 组件挂载后的钩子函数
    
  }
};
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
        <h2>Tab 1 Content</h2>
        <AudioButton soundId="sound1" label="播放声音1" />
      </div>
      <div v-if="currentTab === 'tab2'" class="tab-content tab2">
        <h2>Tab 2 Content</h2>
        <AudioButton soundId="sound2" label="播放声音2" />
      </div>
      <div v-if="currentTab === 'tab3'" class="tab-content tab3">
        <h2>Tab 3 Content</h2>
        <AudioButton soundId="sound3" label="播放声音3" />
      </div>
      <div v-if="currentTab === 'tab4'" class="tab-content tab4">
        <h2>Tab 4 Content</h2>
        <AudioButton soundId="sound4" label="播放声音4" />
      </div>
    </div>
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

  .currentTabContainer{
    display: flex; /* 使用 Flexbox */
    justify-content: space-between; /* 左右对齐 */
    
    
  }

  .tab-content {
    box-sizing: border-box; /* 包含內邊距與邊框 */
    width: 80%;
    height: 50dvh;
    padding: 0.1px;
    margin: 0%;
  /* border: 1px solid #121111;  */
  /* border-radius: 8px;  */
  /* margin-top: 10px;  */
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
@media (min-width: 1366px) {
    .Container {
        background-color: red; 
    }
}

</style>