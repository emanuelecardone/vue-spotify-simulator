<template>
    <nav class="w_60 mx-auto h_10 d-flex flex-wrap justify-content-around align-items-center">
        <a v-for="link,index in content.navLinks" :key="link + index" href="#" 
        class="text-uppercase" :class="{'selected': index === content.currentSection}"
        @click="content.currentSection = index">
            {{link}}
        </a>
    </nav>
</template>

<script>
export default {
    name: 'Nav',
    props: {
        content: Object
    },
    data: function(){
        return{

        }
    }
}
</script>

<style lang="scss" scoped>
@import '../style/variables.scss';

    nav{
        gap: .5rem;
        color: $secondary_color;
        font-size: 1.2rem;
        a{
            display: inline-block;
            color: inherit;
            text-decoration: none;

            &:hover{
                color: $primary_color;
            }

            &.selected{
                border-bottom: 1px solid lime;
                color: $primary_color;
            }
        }
    }
</style>