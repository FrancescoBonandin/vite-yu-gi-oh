<script>
import HeaderComponent from "./components/HeaderComponent.vue";
import MainComponent from "./components/MainComponent.vue";
import FooterComponent from "./components/FooterComponent.vue";
import axios from 'axios'

export default {
  name: "App",
  components: {
    HeaderComponent,
    MainComponent,
    FooterComponent,
  },
  data() {
    return {
      cardsArray:[]
    };
  },
  methods: {},
  created(){
    axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0')
      .then(res=>{
        this.cardsArray=res.data.data
        console.log(res.data.data[0].card_images[0].image_url)
        // .data.data[0].card_images[0].image_url

      }
      )
  },
  mounted(){setTimeout(
    ()=>{console.log(this.cardsArray)},1000)
    
  }
};
</script>

<template>
  <div class="background">
    
    <HeaderComponent />
  
    <MainComponent />
  
    <FooterComponent />
    
  </div>
</template>

<style lang="scss">
@use "assets/scss/main" as *;

.background{
  background-color: $orange-bg;
  min-height: 100vh;
}
</style>
