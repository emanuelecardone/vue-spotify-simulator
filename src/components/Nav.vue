<template>
    <nav class="w_60 mx-auto h_10 d-flex flex-wrap justify-content-around align-items-center">
        <a v-for="link,index in navLinks" :key="link + index" href="#" 
        class="text-uppercase" :class="{'selected': index === selectedLink}"
        @click="selectedLink = index">
            {{link}}
        </a>
    </nav>
</template>

<script>
export default {
    name: 'Nav',
    props: {
        navLinks: Array
    },
    data: function(){
        return{
            // Default
            selectedLink: 0 
        };
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

            &.selected{
                border-bottom: 1px solid lime;
            }
        }
    }
</style>