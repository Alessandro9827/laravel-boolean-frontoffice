<template lang="">
    <div class="">
        <div class="">
            <h1 class="text-center mb-5">
                Lista dei nostri Cocktails belli!
            </h1>
            <div class="container text-center">
                <div class="row justify-content-center">
                    <div class="col-6">
                        <div class="card mb-5" style="width: 40rem;" v-for="cocktail in cocktails" :key="cocktail.id">
                            <img :src="cocktail.image" class="card-img-top" alt="...">
                            <div class="card-body">
                                <h3 class="card-titl fw-bold text-uppercase text-center">{{ cocktail.name }}</h3>
                                <span class="fw-bold text-uppercase pt-4">Ingredienti per prepararlo: </span>
                                <p class="card-text text-center">{{ cocktail.ingredients }}</p>
                                <span class="fw-bold text-uppercase">Prezzo: </span>
                                <p class="card-text text-center price">{{ cocktail.price }} €</p>
                                <a href="#" class="btn btn-primary">Read More</a>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <SingleCard class="card p-0 col-3 mx-4 my-5" v-for="cocktail in cocktails" :key="cocktail.id"
                :name="cocktail.name" :image="cocktail.image" :description="cocktail.description" :linkRoute="{ name: 'single-cocktail', params: { id: cocktail.id}}" linkLabel="Read more..."
            />
            
        </div>
    </div>
</template>

<script>

import SingleCard from '@/components/SingleCard.vue';
import axios from 'axios';

export default {
    name: 'Cocktail',
    data() {
        return {
            cocktails: [],
        }
    },
    methods: {
        getCocktails() {
            axios.get('http://127.0.0.1:8000/api/listCocktails', {
                params: {
                }
            })
                .then((response) => {
                    console.log(response.data.results);
                    this.cocktails = response.data.results;

                })
                .catch(function (error) {
                    console.warn(error);
                })
        }
    },
    components: {
        SingleCard
    },

    created() {
        this.getCocktails();
    }
}

</script>

<style lang="scss" scoped>
div {
    font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
}

.card{
    box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
}

.price{
    color: coral;
    text-shadow: -1px 0 black, 0 1px black, 1px 0 black, 0 -1px black;
    font-size: 27px;
    padding: .5rem 0;
}
</style>