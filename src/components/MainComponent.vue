<script>
export default {
    name: "MainComponent",
    data() {
        return {

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

                    <select class="form-select" aria-label="Default select example">

                        <option selected>Open this select menu</option>

                        <option value="1">One</option>

                        <option value="2">Two</option>

                        <option value="3">Three</option>

                    </select>

                </div>

            </div>

            <div class="row results-found mx-3">

                <div class="col text-light bg-dark">

                    found XX cards

                </div>

            </div>

            <div class="row card-container justify-content-between align-items center mx-3">

                <div class="col-auto">

                    <div class="card" >

                        <img src="" class="card-img-top" alt="">

                        <div class="card-body">

                            <h5 class="card-title">Card title</h5>

                            <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>

                        
                        </div>

                    </div>

                </div>

            </div>

        </div>

        MAIN
    </main>
</template>

<style lang="scss" scoped>

.card-container{
    background-color: white;

 
}

</style>