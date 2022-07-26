<template>
    <section class="spotify w-100 h-100">
        <Header :headerText="data.header" />
        <Main :mainContent="data.main" :songs="data.songs" @setPause="getPause($event)" />
        <Footer :footerContent="data.footer" :user="data.main.username" :currentSongTime="data.songs.currentSongTime" 
        :currentSongDuration="data.songs.currentSongDuration" :currentCommand="data.songs.command" :currentSongVolume="data.songs.currentSongVolume"
        @setCommand="getCommand($event)" @setSongRange="getSongRange($event)" @setVolumeRange="getVolumeRange($event)" />
    </section>
</template>

<script>
import Header from './Header.vue';
import Main from './Main.vue';
import Footer from './Footer.vue';

export default {
    name: 'Spotify',
    components: {
        Header,
        Main,
        Footer
    },
    props: {
        data: Object
    },
    methods: {
        // Pausa
        getPause: function(e){
            this.$emit('setPause', e);
        },
        // Range song
        getSongRange: function(e){
            this.$emit('setSongRange', e);
        },
        // Range volume
        getVolumeRange: function(e){
            this.$emit('setVolumeRange', e);
        }
    }      
}
</script>

<style lang="scss" scoped>

</style>