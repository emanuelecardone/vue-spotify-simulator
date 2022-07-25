<template>
    <section class="spotify w-100 h-100">
        <Header :headerText="data.header" />
        <Main :mainContent="data.main" :songs="data.songs" />
        <Footer :footerContent="data.footer" :user="data.main.username" />
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
    }    
}
</script>

<style lang="scss" scoped>

</style>