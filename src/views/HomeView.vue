<script>
export default {
  name: 'MyComponent', // 组件的名称
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
  <div class="big"></div>
</template>

<style>
.big{
  width: 100%;
  height: 85dvh;
  background-color: purple;
}

/* iPad-PC: 768px - 991px */
@media (min-width: 768px) {
    /* iPad 或較小的桌面專用的 CSS */
    .big{
  background-color: pink;
}
}

/* PC: 992px 以上 */
@media (min-width: 992px) {
    /* 電腦專用的 CSS */
    .big {
        background-color: green; /* 電腦上的背景顏色 */
    }
}


</style>