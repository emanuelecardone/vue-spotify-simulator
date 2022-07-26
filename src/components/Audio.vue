<template>
    <audio ref="audio" :src="sourceString" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>
</template>

<script>
export default {
    name: 'Audio',
    props: {
        source: String,
        pause: String
    },
    data: function(){
        return{
            sourceString: require('../assets/audio/' + this.source + '.mp3'),
            audioHtml: null
        };
    },
    watch:{
        pause: function(){
            if(this.pause === 'pause'){
                this.audioHtml.pause();
            } else{
                this.audioHtml.play();
            }
        }
    },
    methods: {
        getPause: function(e){
            console.log(e)
        }
    },
    created: function(){
    },
    mounted: function(){
        // Partenza canzone
        this.audioHtml = this.$refs.audio;
        this.audioHtml.play();
    }
}
</script>

<style lang="scss" scoped>

</style>