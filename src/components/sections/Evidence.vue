<template>
    <section class="evidence d-flex flex-column">
        <h2 class="mb_50">evidence</h2>
        <div class="evidence_songs w-100 h_90">
            <div class="container-fluid">
                <div class="row row-cols-4">
                    <div v-for="song, index in evidenceSongs" :key="song + '-' + index" class="col">
                        <Card :song="song" :songsData="allSongs" :songIndex="index" />
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
import Card from '../Card.vue';

export default {
    name: 'Evidence',
    components: {
        Card
    },
    props: {
        allSongs: Object,
        evidenceSongs: Array,
        current: Number
    }    
}
</script>

<style lang="scss" scoped>

</style>