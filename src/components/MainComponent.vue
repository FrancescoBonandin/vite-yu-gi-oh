<script>
import {store} from '../store.js'

export default {
    name: "MainComponent",
    components:{
    },
    data() {
        return {
            store,


        }
    },
    methods: {

    }
}
</script>

<template>
    <main>

        <div class="container">

            <div class="row">

                <div class="col-auto px-2 my-3">

                    <h2>{{ store.filteringParam }}</h2>

                    <form @submit.prevent="$emit('search')" action="">
                        
                        <select class="form-select" v-model="store.filteringParam" aria-label="Default select example">
    
                            <option class="text-center"  selected value="">--filter by archetype--</option>
    
                            <option class="text-center" v-for="(singleArchetype,i) in store.archetypeArray" :key="i" :value="singleArchetype.archetype_name">{{ singleArchetype.archetype_name }}</option>
    
    
                        </select>

                        <button type="submit">Filter</button>
                    </form>


                </div>

            </div>

            <div class="row results-found mx-3">

                <div class="col text-light bg-dark">

                    found {{ store.cardsArray.length }} cards

                </div>

            </div>

            <div class="row flex-wrap row-cols-5 card-container justify-content-between align-items-start mx-3 g-2">

                <div v-for="(ygoCard,i) in store.cardsArray" :key="i"  class="col p-3">
                    
                    <div class="col p-3">

                        <div class="card" >

                            <div class="img-container card-img-top">
                                
                                <img :src="ygoCard.card_images[0].image_url" :alt="ygoCard.name">

                            </div>

                            <div class="card-body">

                                <h5 class="card-title">{{ygoCard.name}}</h5>

                                <p class="card-text">{{ ygoCard.archetype }}</p>

                            </div>

                        </div>

                    </div>

                </div>

            </div>

        </div>

        
    </main>
</template>

<style lang="scss" scoped>
@use '../assets/scss/partials/variables'as*;
.card-container{
    background-color: white;
    .img-container{
    width: 100%;

    img{
        width: 100%;
    }
    
    }

    .card-body{
        background-color: $orange-bg;
    }

  
}


</style>