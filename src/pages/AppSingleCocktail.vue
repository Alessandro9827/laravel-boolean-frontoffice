<template lang="">
    <div>
      
  <div class="container">
    <div class="row">
      <h1 class="text-center">{{ cocktail.name }}</h1>
      <img :src="cocktail.image" class="card-image" alt="..." />
      <div class="card-body">
        <p class="card-text">{{ cocktail.description }}</p>
        <p>{{ cocktail.ingredients }}</p>
        <p>{{ cocktail.price }} €</p>
      </div>
    </div>
  </div>

       
    </div>
</template>
<script>
import axios from 'axios';

export default {
  name: 'AppSingleCocktail',
  data() {
    return {
      cocktail: {},
      id: '',
    };
  },
  methods: {
    getCocktail() {
      const id = this.$route.params.id; // Recupera l'ID del cocktail dai parametri della rotta

    
     

      axios.get(`http://127.0.0.1:8000/api/listCocktails/${id}`, {
        params: {}
      })
        .then((response) => {
          // Pulisci i dati della risposta per prevenire XSS se necessario
          // (ad esempio, usando una libreria affidabile come `dompurify`)
          this.cocktail = response.data.results;
        })
        .catch(function (error) {
          console.warn(error);
        });
    },
  },
  created() {
    this.getCocktail();
  },
};
</script>

<style lang="">
    
</style>