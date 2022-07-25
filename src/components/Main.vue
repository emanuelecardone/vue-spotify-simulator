<template>
    <main class="w-100 d-flex pt_130 position-relative">
        <Aside class="position-absolute" />
        <div class="right_main w_85 position-absolute">
            <Nav :navLinks="mainContent.navLinks" />
            <Album />
        </div>
    </main>
</template>

<script>
import Aside from './Aside.vue';
import Album from './Album.vue';
import Nav from './Nav.vue';

export default {
    name: 'Main',
    components: {
        Aside,
        Album,
        Nav
    },
    props: {
        mainContent: Object
    },
    data: function(){
        return{
            
        };
    }
}
</script>

<style lang="scss" scoped>

    main{
        height: calc(100% - 130px);
        background-color: #141922;
        overflow-y: auto;

        .right_main{
            height: calc(100% - 130px);
            top: 130px;
            right: 0;
        }
    }
</style>