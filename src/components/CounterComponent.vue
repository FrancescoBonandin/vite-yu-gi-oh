<script>
import {store} from '../store.js'

export default {
    name: "CounterComponent",
    components:{
    },
    data() {
        return {
            store,


        }
    },
    methods: {

    },
    computed:{
        filteringResultNumber(){
        const filteringResultNumber = this.store.totalApiArr.length
        return filteringResultNumber
        }
    },
}
</script>

<template>
 
    <div class="col text-light bg-dark">

        showing {{ store.cardsArray.length }} cards <span v-if="store.totalApiArr.length > 0">on {{ filteringResultNumber }}</span> 

    </div>

</template>

<style lang="scss" scoped>
</style>