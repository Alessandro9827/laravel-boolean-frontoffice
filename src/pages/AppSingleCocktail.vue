<template lang="">
    <div>
        <h1>
            CIAOOOOOO
        </h1>
        <!-- <SingleCard :name="cocktail.name" :image="cocktail.image" :price="cocktail.price" :description="cocktail.description" :ingredients="cocktail.ingredients"/> -->
    </div>
</template>
<script>
import axios from 'axios';
export default {
    name: 'AppSingleCocktail',
    data: {
        return: {
            cocktail: {},
            id: '',
        }

    },
    // methods: {
    //     getCocktail() {
    //         axios.get(`http://127.0.0.1:8000/api/listCocktails/${this.$route.params.id}`, {
    //             params: {
    //             }
    //         })
    //             .then((response) => {
    //                 console.log(response.data.results);
    //                 this.cocktail = response.data.results;
    //                 console.log(cocktail + 'ciao bello');

    //             })
    //             .catch(function (error) {
    //                 console.warn(error);
    //             })
    //     }
    // },


    // created() {
    //     this.getCocktail();
    // }

}

</script>
<style lang="">
    
</style>