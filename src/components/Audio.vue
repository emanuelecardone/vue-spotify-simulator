<template>
    <audio ref="audio" :src="sourceString" type="audio/mpeg" @timeupdate="setFooter">
      Your browser does not support the audio element.
    </audio>
</template>

<script>
export default {
    name: 'Audio',
    props: {
        source: String,
        command: String,
        currentRange: String,
        currentVolume: String
    },
    data: function(){
        return{
            sourceString: require('../assets/audio/' + this.source + '.mp3'),
            audioHtml: null
        };
    },
    watch:{
        command: function(){
            if(this.command === 'pause'){
                this.audioHtml.pause();
              // Debug  
            } else if(this.command === 'song range' || this.command === 'song-range'){
                this.audioHtml.currentTime = this.audioHtml.duration / 100 * parseInt(this.currentRange);
            } else if(this.command === 'volume range' || this.command === 'volume-range'){
                this.audioHtml.volume = parseInt(this.currentVolume) / 100;
                console.log(this.currentVolume, this.audioHtml.volume)
            } else if(this.command === 'play' || this.command === ''){
                this.audioHtml.play();
            }
        }
    },
    methods: {
        // Invio durata al footer
        setFooter: function(){
            this.$emit('setFooter', {
                time: this.$refs.audio.currentTime,
                duration: this.$refs.audio.duration
            });
        }
    },
    created: function(){
    },
    mounted: function(){
        // Partenza canzone
        this.audioHtml = this.$refs.audio;
        this.audioHtml.play();
        this.audioHtml.volume = parseInt(this.currentVolume) / 100;
    }
}
</script>

<style lang="scss" scoped>

</style>