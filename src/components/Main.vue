<template>
    <main class="w-100 d-flex pt_130 position-relative">
        <Aside :asideContent="mainContent.aside" :username="mainContent.username" class="position-absolute" />
        <div class="right_main w_85 position-absolute">
            <Nav :content="mainContent" />
            <div class="sections_wrapper w-100 h_90 p-5">
                <!-- Stampato quello corrispondente all'index "currentSection" -->
                <Evidence v-if="mainContent.currentSection === 0" :allSongs="songs" :evidenceSongs="songs.evidence" 
                :current="songs.currentSong" @setPause="getPause($event)" />
                <Podcast v-else-if="mainContent.currentSection === 1" />
                <Leaderboards v-else-if="mainContent.currentSection === 2" />
                <Mood v-else-if="mainContent.currentSection === 3" />
                <News v-else-if="mainContent.currentSection === 4" />
                <Discover v-else-if="mainContent.currentSection === 5" />
            </div>
        </div>
    </main>
</template>

<script>
import Aside from './Aside.vue';
import Nav from './Nav.vue';
import Discover from './sections/Discover.vue';
import News from './sections/News.vue';
import Evidence from './sections/Evidence.vue';
import Leaderboards from './sections/Leaderboards.vue';
import Mood from './sections/Mood.vue';
import Podcast from './sections/Podcast.vue';

export default {
    name: 'Main',
    components: {
        Aside,
        Nav,
        Discover,
        News,
        Evidence,
        Leaderboards,
        Mood,
        Podcast
    },
    props: {
        mainContent: Object,
        songs: Object
    },
    data: function(){
        return{
            
        };
    },
    methods: {
        getPause: function(e){
            this.$emit('setPause', e);
        }
    }  
}
</script>

<style lang="scss" scoped>
@import '../style/variables.scss';

    main{
        height: calc(100% - 130px);
        background-color: #141922;

        .right_main{
            height: calc(100% - 130px);
            top: 130px;
            right: 0;

            .sections_wrapper{

                & > section{
                    width: 100%;
                    height: 100%;
                    display: flex;
                    justify-content: center;
                    align-items: center;
                    text-transform: uppercase;
                    color: $primary_color;
                    overflow-y: auto;
                }
            }   
        }
    }
</style>