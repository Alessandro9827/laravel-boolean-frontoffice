<template lang="">
    <div>
        <div class="card-body">
            <img v-if="image" :src="image" class="card-img-top mb-3" :class="fullLength ? '' : 'image-preview'" alt="...">

            <h1 class="card-title mb-3">
                {{ name }}
            </h1>
            <p class="card-text">
                {{ description }}
            </p>
            <p class="card-text">
                {{ ingredients }}
            </p>
            <p class="card-text">
                {{ price }} €
            </p>
            <div class="w-100 d-flex mb-3">
                <router-link :to="linkRoute" class="btn btn-primary">
                    {{ linkLabel }}
                </router-link>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {

        }
    },
    props: {
        name: {
            required: true,
            type: String,
        },
        price: {
            required: true,
            type: Number,
        },
        image: {
            required: true,
            type: String,
        },
        description: {
            required: true,
            type: String,
        },
        ingredients: {
            required: true,
            type: String,
        },
        linkRoute: {
            required: false,
            type: [Object, String]
        },
        linkLabel: {
            required: false,
            type: String,
        },
        fullLength: {
            required: false,
            type: Boolean,
        },
    }
}
</script>
<style lang="scss" scoped></style>