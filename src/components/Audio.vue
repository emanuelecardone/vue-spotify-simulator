<template>
    <audio ref="audio" :src="sourceString" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
</template>

<script>
export default {
    name: 'Audio',
    props: {
        source: String
    },
    data: function(){
        return{
            sourceString: require('../assets/audio/' + this.source + '.mp3')
        };
    },
    created: function(){
        
    },
    mounted: function(){
        // Partenza canzone
        this.$refs.audio.load();
        this.$refs.audio.play();
    }
}
</script>

<style lang="scss" scoped>

</style>