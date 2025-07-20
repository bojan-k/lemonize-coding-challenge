<script>
import Product from "./Product.vue";

export default {
    props: {
        products: Array,
    },
    components: {
        Product,
    }
}
</script>

<template>
    <div>
      <Product v-for="product in products" :key="product.id" :name="product.title"/>
    </div>
</template>

<style lang="css" scoped>
@import "tailwindcss";

div {
    display       : flex;
    flex-direction: column;
}
</style>