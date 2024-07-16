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

const playAudio = () => {
  const audioResource = props.audioResourceList.find(resource => resource.id === props.soundId);
  if (audioResource) {
    const audio = new Audio(audioResource.src);
    audio.volume = audioResource.volume;
    audio.play();
  }
};
</script>

<template>
  <button @click="playAudio">{{ label }}</button>
</template>

<style scoped>
button {
  padding: 10px 20px;
  margin: 5px;
  font-size: 16px;
  cursor: pointer;
}
</style>