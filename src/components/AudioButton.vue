<script>
export default {
    props: {
        soundId: {
            type: String,
            required: true
        },
        label: {
            type: String,
            required: true
        }
    },
    methods: {
        playAudio() {
            let audioResource = this.$root.audioResourceList.find(resource => resource.id === this.soundId);
            if (audioResource) {
                let audio = new Audio(audioResource.src);
                audio.volume = audioResource.volume;
                audio.play();
            }
        }
    }
}
</script>

<template lang="">
    <button @click="playAudio">{{ label }}</button>
</template>

<style lang="">
    
</style>