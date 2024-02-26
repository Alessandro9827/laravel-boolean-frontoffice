<template lang="">
    <div class="container">
        <div class="row">
            <h1 class="text-center">
                Lista dei nostri Cocktails belli!
            </h1>
            <section class="row justify-content-center">
            <div class="col-12">
            </div>
            <article class="d-flex">
                <SingleCard class="card p-0 col-3 mx-4 my-5" v-for="cocktail in cocktails" :key="cocktail.id" :id="cocktail.id" :name="cocktail.name" :image="cocktail.image" :price="cocktail.price" :description="cocktail.description" :ingredients="cocktail.ingredients" :linkRoute="{ name: 'single-cocktail', params:{id:cocktail.id}}" linkLabel="Read more.."/>
            </article>
            {{ cocktails[0].name }}
        </section>
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
</style>