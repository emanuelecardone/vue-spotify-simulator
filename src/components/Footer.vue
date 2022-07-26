<template>
    <footer class="w-100 h_130p position-relative d-flex justify-content-between align-items-center px-2">
        <!-- LEFT -->
        <div class="left_footer w-25 h-100 d-flex justify-content-between align-items-center text-white">
            <div class="song_box w_60 h-100 d-flex justify-content-between align-items-center">
                <div class="w_50p h_50p d-flex me-3 justify-content-center align-items-center border border-2 border-white fs-6">
                album
                </div>
                <h5 class="fs-5">
                    Nome canzone <br>
                    <span class="fs-6">{{user}}</span>
                </h5>
            </div>     
            <div class="left_footer_icons">
                <ul class="d-flex align-items-center h-100">
                    <li v-for="icon, index in footerContent.icons.left" :key="icon + index">
                        <a href="#">
                            <i :class="'far secondary ms-4 fs-3 ' + icon"></i>
                        </a>
                    </li>
                </ul>
                 
            </div> 
        </div>
        <!-- MIDDLE -->
        <div class="middle_footer w-50 h-100">
            <div class="middle_icons w-100 h-50 d-flex align-items-center">
                <ul class="w-100 d-flex justify-content-center align-items-center h-100">
                    <li v-for="icon,index in footerContent.icons.middle" :key="icon + index">
                        <a href="#">
                            <i :class="icon"></i>
                        </a>
                    </li>
                </ul>
            </div>
            <div class="middle_range_box w-100 h-50 d-flex justify-content-center align-items-center">
                <input type="range" ref="song_range" @input="songRange" id="song_range" 
                :value="rangeValue" name="song_range" class="w-50">
            </div>
        </div>
        <!-- RIGHT -->
        <div class="right_footer w-25 h-100 d-flex justify-content-center align-items-center">
            <div class="right_footer_icons me-5 h-100">
                <ul class="d-flex align-items-center h-100">
                    <li v-for="icon, index in footerContent.icons.right" :key="icon + index">
                        <a href="#">
                            <i :class="'fas secondary mx-2 fs-3 ' + icon"></i>
                        </a>
                    </li>
                </ul>
            </div>
            <input type="range" ref="volume" id="volume" value="50" name="volume">
        </div>
    </footer>   
</template>

<script>
export default {
    name: 'Footer',
    props: {
        footerContent: Object,
        user: String,
        currentSongTime: Number,
        currentSongDuration: Number,
        currentCommand: String
    },
    data: function(){
        return{
            // ranges
            song_range: null,
            volume: null,
            rangeValue: 0
        };
    },
    watch: {
        currentSongTime: function(){
            this.rangeValue = 100 / this.currentSongDuration * this.currentSongTime;
        }
    },
    methods: {
        // Set range song
        songRange: function(e){
            // Debug ripetizione command (altrimenti non funziona il watch)
            const debugRange = this.currentCommand === 'song range' ? 'song-range' : 'song range';
            this.$emit('setSongRange', {
                command: debugRange,
                value: e.target.value
            });
        },
        // Set range volume
        volumeRange: function(){

        }
    },
    mounted: function(){
        // Ranges mounted 
        this.song_range = this.$refs.song_range;
        this.volume = this.$refs.volume;
    }
}
</script>

<style lang="scss" scoped>
@import '../style/variables.scss';

    footer{
        background-color: #282828;
        z-index: 3000;

        a{

            &:hover i{
                color: $primary_color;
            }
        }

        .secondary{
            color: $secondary_color;
        }

        .middle_footer{

            i{
                font-size: 2rem;
                color: $primary_color;
                margin: 0 20px 0;
                
                &:hover{
                    color: lime;
                }

                &.fa-play-circle{
                    font-size: 3rem;

                    @media screen and (max-width: 992px){
                        font-size: 2rem;
                    }
                }

                @media screen and (max-width: 992px){
                    font-size: 1.5rem;
                    margin: 0 10px 0;
                }
            }
        }

        .right_footer_icons,
        .left_footer_icons{
            @media screen and (max-width: 992px){
                display: none;
            }
        }

        #volume,
        #song_range{
            cursor: pointer;
        }

        #volume{
            width: 30%;
            min-width: 50px;

            @media screen and (max-width: 992px){
                min-width: auto;
                width: 80%;
            }
        }
    }
</style>