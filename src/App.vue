<script>
import HeaderComponent from "./components/HeaderComponent.vue";
import MainComponent from "./components/MainComponent.vue";
import LoadingScreen from "./components/LoadingScreen.vue";
import axios from 'axios'
import {store} from './store.js'

export default {
  name: "App",
  components: {
    HeaderComponent,
    MainComponent,
    LoadingScreen,
  },
  data() {
    return {
    store,
    };
  },
  methods: {},
  // created(){
  //   axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0')
  //     .then(res=>{
  //       this.store.cardsArray=res.data.data
  //       console.log(res.data.data[0].card_images[0].image_url)
  //       // .data.data[0].card_images[0].image_url

  //     }
  //     )
  // },
  mounted(){
    // necessario per vedere il bonus
    setTimeout(
      ()=>{axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0')
        .then(res=>{
          this.store.cardsArray=res.data.data
          console.log(res.data.data[0].card_images[0].image_url)
          // .data.data[0].card_images[0].image_url

        }
        )},8000)
    
  }
};
</script>

<template>
  <div class="background">
    
    <HeaderComponent />
  
    <LoadingScreen v-if="store.cardsArray.length==0"/>

    <MainComponent v-else />
    
  </div>
</template>

<style lang="scss">
@use "assets/scss/main" as *;

.background{
  background-color: $orange-bg;
  min-height: 100vh;
}
</style>
