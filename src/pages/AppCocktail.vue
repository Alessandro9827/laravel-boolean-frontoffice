<template lang="">
    <div class="container">
        <div class="row">
            <h1 class="text-center">
                Lista dei nostri Cocktails!
            </h1>
            <section class="row justify-content-center">
            <div class="col-12">
            </div>
            <SingleCard class="card p-0 col-3 mx-4 my-5" v-for="cocktail in cocktails" :key="cocktail.id"
                :title="cocktail.name" :image="cocktail.image" :description="cocktail.description" :linkRoute="{ name: 'single-post', params: { id: cocktail.id}}" linkLabel="Read more..."
            />
        </section>
        </div>
    </div>
</template>

<script>

import SingleCard from '@/components/SingleCard.vue';
import axios from 'axios';

export default {
    name: 'PostList',
    data(){
        return{
            posts: [],
        }
    },
    methods:{
        getPosts(){
            axios.get('http://127.0.0.1:8000/api/posts', {
                params: {
                }
            })
            .then((response) => {
                console.log(response.data.results.data);
                this.posts = response.data.results.data;

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
        this.getPosts();
    }
}

</script>

<style lang="scss" scoped>

div{
    font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
}



</style>