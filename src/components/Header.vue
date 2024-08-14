<script>
import { RouterLink, RouterView } from 'vue-router'
export default {
    data() {
        return {
        }
    },
    components: {
        RouterLink,
    },
}
</script>

<template>
    <h1 class="title_JP">周防有希ボタン</h1>
    <h1 class="title_EN">Suō Yuki Button</h1>
    <!-- <div class="headerShow"> -->
        <!-- <RouterLink to="/" class="routerItem">周防有希ボタン</RouterLink> -->
        

        <!-- <RouterLink to="AboutView" class="routerItem">AboutView</RouterLink> -->
    <!-- </div> -->
</template>


<style scoped lang="scss">

.title_JP {
    margin: 0 auto 0.3rem auto;
    margin-top: 5dvh;
    display: flex;
    justify-content: center;
    align-content:center;
        font-family: 'Press Start 2P', 'Kosugi Maru', cursive;
        color: rgba(246, 75, 95, 0.992);
        font-size: 3rem;
        text-decoration: none;
        text-shadow: 4px 3px 0px #fff, 9px 8px 0px rgba(0, 0, 0, 0.15);
    }

    .title_EN{
    margin: 0 auto 0.3rem auto;
    margin-top: 5dvh;
    display: flex;
    justify-content: center;
    align-content:center;
        font-family: 'Press Start 2P', 'Kosugi Maru', cursive;
        color: rgba(246, 75, 95, 0.992);
        font-size: 1.5rem;
        text-decoration: none;
        text-shadow: 4px 3px 0px #fff, 9px 8px 0px rgba(0, 0, 0, 0.15);
    }

.headerShow {
    width: 100%;
    min-height: 15dvh;
    background-color: pink;
    display: flex;
    justify-content: center;
    align-content:center;
    letter-spacing: 2px;
    // font-family: 'Press Start 2P', 'keifontregular', 'Kosugi Maru', cursive;

    

    a {
        // margin-right: 20px;
        padding-top: 5dvh;

        // &:hover {
        //     border-radius: 10px;
        //     background-color: rgba(129, 255, 196, 0.27);
        //     font-size: 40px;
        //     color: black;
        //     box-shadow: 0px 0px 30px 4px rgba(0, 0, 0, 0.2);
        // }

        // &:active {
        //     border-radius: 10px;
        //     background-color: rgba(0, 0, 0, 0.344);
        // }
    }
}


/* PC: 1200px 以上 */
@media (min-width: 1200px) {

    .title_JP {
        margin-top: 5.5dvh;
        font-size: 5rem;
        
    }
    
    .title_EN {
        margin-top: 5.5dvh;
        font-size: 3rem;
        
    }

  
}
</style>
