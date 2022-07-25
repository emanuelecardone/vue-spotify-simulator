<template>
    <a href="#" class="btn page_btn">{{message}}</a>
</template>

<script>
export default {
    name: 'Button',
    props: {
        message: String
    }    
}
</script>

<style lang="scss" scoped>
@import '../style/mixins.scss';

    .page_btn{
        @include page_button;
    }
</style>