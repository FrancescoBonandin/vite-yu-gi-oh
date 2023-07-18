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
  methods: {
    getResponse(){axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=40&offset=0')
      .then(res=>{
        this.store.cardsArray=res.data.data
        // console.log(res.data.data[0].card_images[0].image_url)

      }
      )
    },
    getArchetype(){axios.get('https://db.ygoprodeck.com/api/v7/archetypes.php')
      .then(res=>{
      
        this.store.archetypeArray=res.data
        
        // console.log(res.data)
      }
      )
    },
    filtering(){   
       axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php',{
        params:{
          archetype:this.store.filteringParam,

        }
      }
      )
        .then(res=>{
        
          this.store.totalApiArr=res.data.data
          
          // console.log(res)
        }
        )
      

      axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=40&offset=0',{
        params:{
          archetype:this.store.filteringParam,

        }
      }
      )
        .then(res=>{
        
          this.store.cardsArray=res.data.data
          
          // console.log(res)
        }
        )
        .catch(err=>{
          if(this.store.filteringParam==''){

          }
          else if(this.store.filteringParam!=''&& this.store.cardsArray.length==0){
            this.store.cardsArray=[]
          }
        })
    }
  },

  created(){
    this.getArchetype()
  },
  mounted(){
    // necessario per vedere il bonus
    setTimeout(()=>{this.getResponse()},4000)

  },
};
</script>

<template>
  <div class="background">
    
    <HeaderComponent/>
  
    <LoadingScreen v-if="store.cardsArray.length==0"/>

    <MainComponent v-else  @search="filtering()" />
    
  </div>
</template>

<style lang="scss">
@use "assets/scss/main" as *;

.background{
  background-color: $orange-bg;
  min-height: 100vh;
}
</style>
