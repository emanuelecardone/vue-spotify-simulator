<template>
  <div id="app" class="w-100 vh-100">
    <Spotify :data="datas" />
  </div>
</template>

<script>
import Spotify from './components/Spotify.vue';

export default {
  name: "App",
  components: {
    Spotify
  },
  data: function(){
    return{
      // Tutti i dati dell'App
      datas: {
        header:{
          button: 'effettua l\'upgrade'
        },
        main: {
          // Nav main
          navLinks: [
            'in evidenza',
            'podcast',
            'classifiche',
            'generi e mood',
            'nuove uscite',
            'scopri'
          ]
        }
      }
    };
  }
};
</script>

<style lang="scss">
@import './style/variables.scss';
@import './style/mixins.scss';
@import './style/general.scss';
@import './style/size-space.scss';
@import './style/utilities.scss';

</style>
