<script>
import {store} from '../store.js'


export default {
  name: "LoadingScreen",
  data() {
    return {
    store,
    loadingMessage:null,
    };
  },
  methods: {
    Loading(){
        this.loadingMessage =''
        const clock=setInterval(()=>{
            this.loadingMessage +='.';

            if(this.store.cardsArray.length==20){
                clearInterval(clock)
            }

            else if (this.loadingMessage.length >3) {
                this.loadingMessage =''
            }
        },1000)
    }
  },

  mounted(){
    this.Loading()
  }

};
</script>

<template>

    <div class="container">

        <div class="row justify-content-center align-items-center">

            <div class="col text-center">

                <h2>
                   {{ `Loading Results ${loadingMessage}` }}
                </h2>

            </div>
            
        </div>

    </div>

</template>

<style lang="scss" scoped>
</style>