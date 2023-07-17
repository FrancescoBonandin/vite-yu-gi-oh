<script>
export default {
    name: "HeaderComponent",
    data() {
        return {

        }
    },
    methods: {

    }
}
</script>

<template>
    <header>

        <div class="container mx-1">

            <div class="row align-items-center">
                
                <div class="col-auto">

                    <div class="img-container">
            
                        <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/11/Yu-Gi-Oh%21_%28Logo%29.jpg/800px-Yu-Gi-Oh%21_%28Logo%29.jpg" alt="">
            
                    </div>
                
                </div>

                <div class="col-auto">

                    <h1>
                        Yu-Gi-Oh API
                    </h1>   
                
                </div>

            </div>

        </div>

    </header>
</template>

<style lang="scss" scoped>
header{

    background-color: white;
    border-bottom: solid 1px black;
    .img-container{
        height: 2rem;

        img{
            height: 100%;
        }
    }
}
</style>