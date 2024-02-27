<template lang="">
  <div class="container">
    <div class="row">
      <h1 class="text-center">Lista dei nostri Cocktails belli!</h1>
      <section class="row justify-content-center">
        <article class="col-4 card mb-2 me-2 p-0" v-for="cocktail in cocktails">
          <img
            :src="cocktail.image"
            class="card-image"
            alt="..."
          />
          <div class="card-body">
            <h5 class="card-title">{{ cocktail.name }}</h5>
            <p class="card-text">
              {{ cocktail.description }}
            </p>
            <p>{{ cocktail.ingredients }}</p>
            <p>{{ cocktail.price }} €</p>
            <div class='d-flex justify-content-center' >

                <div class="d-flex justify-content-center">
              <router-link :to="{ name: 'single-cocktail', params: { id: cocktail.id } }">
                <button class="btn btn-primary">More.</button>
              </router-link>
            </div>
        </div>
          </div>
        </article>
      </section>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import AppSingleCocktail from "./AppSingleCocktail.vue";

export default {
  name: "Cocktail",

  data() {
    return {
      cocktails: [],
    };
  },
  methods: {
    getCocktails() {
      axios
        .get("http://127.0.0.1:8000/api/listCocktails", {
          params: {},
        })
        .then((response) => {
          console.log(response.data.results);
          this.cocktails = response.data.results;
        })
        .catch(function (error) {
          console.warn(error);
        });
    },
  },
  components:{
      AppSingleCocktail,
  },

  created() {
    this.getCocktails();
  },
};
</script>

<style lang="scss" scoped>
div {
  font-family: "Trebuchet MS", "Lucida Sans Unicode", "Lucida Grande",
    "Lucida Sans", Arial, sans-serif;
}

.card-image{
    width: 100%;
    height: 30rem;
    object-fit: cover;
}
</style>
