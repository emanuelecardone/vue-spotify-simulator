<template>
    <header class="w_85 h_130p d-flex justify-content-end align-items-center p-2">
        <Button class="text-uppercase" :message="headerText.button" />
    </header>
</template>

<script>
import Button from './Button.vue';

export default {
    name: 'Header',
    components: {
        Button
    },
    props: {
        headerText: Object
    }    
}
</script>

<style lang="scss" scoped>

    header{
        background-color: rgba($color: #000000, $alpha: .7);
        position: fixed;
        top: 0;
        right: 0;
        z-index: 2000;
    }
</style>