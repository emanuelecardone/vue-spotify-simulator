<template>
    <div class="card w-50 p-2 pt-3 mx-auto">
        <img :src="require('../assets/img/songs/evidence/' + song.image + '.png')" class="card-img-top w_90 mx-auto" :alt="'immagine di ' + song.name">
        <div class="card-body">
            <h5 class="card-title">{{song.name}}</h5>
            <p class="card-text">{{song.artist}}</p>
            <a href="#" class="btn btn-primary mt-2">
                <i @click="setSong" class="fa-solid fa-play fs-4"></i>
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
    methods: {
        // Set canzone (index)
        setSong: function(){
            this.songsData.currentSong = this.songIndex;
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