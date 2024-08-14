<script setup>
import { inject, ref } from 'vue';

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

// Injecting the global audio manager
const audioManager = inject('audioManager');
const isPlaying = ref(false);

const playAudio = () => {
  const audioResource = props.audioResourceList.find(resource => resource.id === props.soundId);
  if (audioResource) {
    if (audioManager.currentAudio.value) {
      // Check if the currently playing audio is the same as the new audio
      if (audioManager.currentAudio.value.src !== audioResource.src) {
        audioManager.stopCurrentAudio(); // Stop the currently playing audio if different
      } else {
        // Restart the same audio if it's already playing
        audioManager.currentAudio.value.currentTime = 0; // Reset to the beginning
        audioManager.currentAudio.value.play(); // Play again
        return; // Exit playAudio to avoid creating a new Audio instance
      }
    }

    // Create a new Audio instance
    const newAudio = new Audio(audioResource.src);
    newAudio.volume = audioResource.volume;

    // Update the global audio manager
    audioManager.currentAudio.value = newAudio;

    newAudio.play();
    isPlaying.value = true;

    newAudio.addEventListener('ended', () => {
      isPlaying.value = false;
    });
  }
};

const handleButtonClick = () => {
  if (isPlaying.value && audioManager.currentAudio.value && audioManager.currentAudio.value.src === props.audioResourceList.find(resource => resource.id === props.soundId).src) {
    // If the same audio is already playing, reset and play again
    audioManager.currentAudio.value.currentTime = 0; // Reset to the beginning
    audioManager.currentAudio.value.play(); // Play again
  } else {
    // If not playing or different audio, play the new audio
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
  border-width: 0px;
  background-color: rgb(245, 97, 122);
  color: white;
  font-family: 'Noto Sans JP', sans-serif;
  box-shadow: 0 9px #bd4646;
}

.button:hover {background-color: rgb(244, 70, 99)}

.button:active {
  background-color: rgb(244, 70, 99);
  box-shadow: 0 5px #bd4646;
  transform: translateY(4px);
}

</style>