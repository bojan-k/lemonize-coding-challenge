<script>
import ProductList from './components/ProductList.vue'

export default {
    data() {
        return {
            products: [],
        };
    },
    components: {
      ProductList,
    },
    mounted() {
        fetch('https://dummyjson.com/products').then(res => res.json()).then(json => this.products = json.products);
    }
}
</script>

<template>
  <main>
    <h1 class="text-3xl font-bold underline">
        Hello world!
    </h1>
    <ProductList :products="products"/>
  </main>
</template>

<style scoped>
@import "tailwindcss";
</style>
