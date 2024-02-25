<template lang="">
    <main class=" mt-3 mb-5">
    <div class="">
    <div class="row ">
      <div class="col-6 p-0">
        <img src="https://www.coqtailmilano.com/wp-content/uploads/2021/04/cocktail-caraibici-ricette-ingredienti-preparazione-Coqtail-Milano.jpg" alt="" class="">
      </div>
      <div class="col-6 bg-body-tertiary border border-1 vertical-align-center">
        <h2>
          PROVA IL NOSTRO BOX DI COCKTAIL
        </h2>
        <p>
          Sei iconici cocktail in busta pronti da bere, racchiusi in un elegante cofanetto trasportabile ovunque. Perfetto come idea regalo per chi ama sorseggiare il proprio drink preferito in compagnia. Prova anche una delle nostre ultime uscite, puoi trovarlo nella sezione Cocktails.
        </p>
      </div>
    </div>
    </div>
    <div>
      <h2 class="text-center mt-5">
          I nostri Cocktail più amati
      </h2>
      <SingleCard class="card p-0 col-3 mx-4 my-5" v-for="cocktail in cocktails" :key="cocktail.id"
                :title="cocktail.name" :image="cocktail.image" :price="cocktail.price" :linkRoute="{ name: 'single-post', params: { id: cocktail.id}}" linkLabel="Read more..."
            />
    </div>
    </main>
</template>

<script>
import SingleCard from '@/components/SingleCard.vue';
import axios from 'axios';
export default {
    name: 'Homepage',
    data(){
        return{
            cocktails: [],
        }
    },
    methods:{
        getCocktails(){
            axios.get('http://127.0.0.1:8000/api/listCocktails', {
                params: {
                }
            })
            .then((response) => {
                console.log(response.data.results.data);
                console.log(this.cocktails);
                this.cocktails = response.data.results.data;
            })
            .catch(function (error) {
                console.warn(error);
            })
        }
    },
    components:{
        SingleCard
    },
    created(){
        this.getCocktails();
    }
}
</script>

<style lang="scss" scoped>

main{
    font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
}

div.row img{
    width: 100%;
}

div.col-6{
  padding-top: 7.5rem;
}

</style>