<template>
  <div id="app" class="w-100 vh-100">
    <Spotify :data="datas" @setPause="getPause($event)" />
    <Audio v-if="datas.songs.currentSong !== null && datas.songs.playing" 
    :source="datas.songs.evidence[datas.songs.currentSong].source" :pause="datas.songs.command"
    style="width: 0; height: 0;"  />
  </div>
</template>

<script>
import Spotify from './components/Spotify.vue';
import Audio from './components/Audio.vue';

export default {
  name: "App",
  components: {
    Spotify,
    Audio
  },
  data: function(){
    return{
      // Tutti i dati dell'App
      datas: {
        songs:{
          // per stop
          command: '',
          currentSongTime: 0,
          currentSong: null,
          playing: false,
          // Debug cambio canzone (cambiato al click card)
          nextSong: null,
          // Canzoni per ogni sezione
          evidence:[
            {
              name: 'make me believe',
              artist: 'jamie berry',
              image: 'make-me-believe',
              source: 'makemebelieve',
              section: 'evidence'
            },
            {
              name: 'prohibition',
              artist: 'jamie berry',
              image: 'prohibition',
              source: 'prohibition',
              section: 'evidence'
            }
          ]
        },
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
          ],
          // Sezione attuale
          currentSection: 0,
          // Username (da fare dopo)
          username: 'profilo',
          // Aside
          aside: {
            // Icone
            icons: [
              {
                name: 'home',
                icon: 'fa-house'
              },
              {
                name: 'cerca',
                icon: 'fa-magnifying-glass'
              }
            ],
            // Icona selezionata
            selectedIcon: 0,
            // Playlist
            playlists: [
              'playlist 1',
              'playlist 2',
              'playlist 3',
              'playlist 4',
              'playlist 5',
              'playlist 6',
              'playlist 7'
            ],
            // Playlist selezionata
            selectedPlaylist: null
          }
        },
        footer: {
          icons: {
            left: ['fa-heart', 'fa-folder'],
            middle: ['fas fa-random', 'fas fa-step-backward', 'far fa-play-circle', 'fas fa-step-forward', 'fas fa-redo-alt'],
            right: ['fa-list-ul', 'fa-desktop', 'fa-volume-up']
          }
        }
      }
    };
  },
  methods: {
    getPause: function(e){
      this.datas.songs.command = e;
    }
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
