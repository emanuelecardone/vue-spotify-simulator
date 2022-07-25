<template>
    <div class="card w-50 pt-3 mx-auto">
        <img :src="require('../assets/img/songs/evidence/' + song.image + '.png')" class="card-img-top w_90 mx-auto" :alt="'immagine di ' + song.name">
        <div class="card-body">
            <h5 class="card-title">{{song.name}}</h5>
            <p class="card-text">{{song.artist}}</p>
            <a href="#" class="btn btn-primary rounded-circle mt-2">
                <i class="fa-solid fa-play"></i>
            </a>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Card',
    props: {
        song: Object
    }
}
</script>

<style lang="scss" scoped>
@import '../style/variables.scss';

    .card{

        background-color: rgba($color: #000000, $alpha: .7);

        &-title{
            color: $primary_color;
        }
        &-text{
            color: $secondary_color;
        }
    }
</style>