<template>
    <div class="card w_70 p-2 pt-3 mx-auto">
        <img :src="require('../assets/img/songs/evidence/' + song.image + '.png')" class="card-img-top w_90 mx-auto" :alt="'immagine di ' + song.name">
        <div class="card-body">
            <h5 class="card-title">{{song.name}}</h5>
            <p class="card-text">{{song.artist}}</p>
            <a @click="setSong" href="#" class="btn btn-primary mt-2">
                <i  class="fa-solid fa-play fs-4 position-relative"></i>
            </a>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Card',
    props: {
        song: Object,
        songIndex: Number,
        songsData: Object
    },
    data: function(){
        return{
            // Debug 0.001s
            playClock: null,
            pause: ''
        };
    },
    methods: {
        // Set canzone (index)
        setSong: function(){
            // Debug cambio src
            // Settato nextSong con la canzone scelta
            this.songsData.nextSong = this.songIndex;
            // Inizio (quando current è null)
            if(this.songsData.currentSong === null){
                this.songsData.currentSong = this.songsData.nextSong;
                this.songsData.playing = true;
              // toggle click sulla stessa card  
            } else if(this.songsData.nextSong === this.songsData.currentSong){
                this.pause = this.pause === '' ? 'pause' : '';
                this.$emit('setPause', this.pause);
              // caso cambio canzone (debuggato col ritardo di 0.001s altrimenti non calcola il cambio al v-if)  
            } else if(this.songsData.nextSong !== this.songsData.currentSong){
                this.songsData.playing = false;
                this.songsData.currentSong = this.songsData.nextSong;
                this.playClock = setTimeout(() => {this.songsData.playing = true;}, 1)
                console.log(this.songsData)
            }
            // this.songsData.playing = !this.songsData.playing;
        }
    }
}
</script>

<style lang="scss" scoped>
@import '../style/variables.scss';

    .card{

        border-radius: 20px;
        cursor: pointer;

        background-color: rgba($color: #000000, $alpha: .7);

        &-title{
            color: $primary_color;
        }
        &-text{
            color: $secondary_color;
        }

        &:hover{
            background-color: darken($secondary_color, 30%);
        }

        .btn-primary{

            width: 40%;
            padding: 10px 20px;

            &:hover{
                background-color: lime;
            }
        }
    }
</style>