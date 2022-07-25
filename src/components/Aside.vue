<template>
    <aside class="w_15 h-100 bg_black d-flex flex-column justify-content-start align-items-start pt-5 px-4 pb-3">
        <img class="w_150p" src="../assets/img/logo.svg" alt="logo">
        <div class="icons w-100">
            <ul class="mt_60">
                <li v-for="icon, index in asideContent.icons" :key="icon.name">
                    <a href="#" class="fs-3 my-2" :class="{'primary': asideContent.selectedIcon === index}">
                        <i :class="'me-3 fa-solid ' + icon.icon"></i>
                        <span class="text-capitalize">{{icon.name}}</span>
                    </a>
                </li>
            </ul>
        </div>
        <div class="playlist w-100 flex-grow-1 mt_40">
            <h4 class="text-white fs-2 text-uppercase mb-3">Playlists</h4>
            <ul class="playlist_list fs-3">
                <li class="my-2 text-capitalize" v-for="playlist, index in asideContent.playlists" :key="playlist">
                    <a href="#" :class="{'primary': asideContent.selectedPlaylist === index}">{{playlist}}</a>
                </li>
            </ul>
        </div>
        <div class="install w-100 d-flex align-items-center">
            <img src="../assets/img/download.svg" alt="download" class="w_20p">
            <a href="#" class="ms-3 fs-4">Installa app</a>
        </div>
        <div class="line my-1"></div>
        <div class="user d-flex align-items-center">
            <img src="../assets/img/profile.svg" alt="download" class="w_30p h_30p me-2 border border-1 border-white rounded-circle">
            <h4 class="text-white my-2 text-uppercase fs-3">{{username}}</h4>
        </div>
    </aside>
</template>

<script>
export default {
    name: 'Aside',
    props: {
        asideContent: Object,
        username: String
    }    
}
</script>

<style lang="scss" scoped>
@import '../style/variables.scss';

    aside{
        left: 0;
        top: 0;
        color: $secondary_color;
        min-width: 250px;
        a{
            color: inherit;
            text-decoration: none;
            display: inline-block;

            &:hover{
                color: $primary_color;
            }

            &.primary{
                color: $primary_color;
            }
        }

        .playlist{
            min-height: 170px;
            overflow-y: auto;

            &_list{
               
            } 
        }

        .line{
            width: 100%;
            height: 3px;
            background-color: $secondary_color;
        }
    }
</style>