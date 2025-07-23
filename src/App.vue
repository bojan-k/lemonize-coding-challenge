<script>
import ProductFilter from './components/ProductFilter.vue'
import ProductList   from './components/ProductList.vue'

export default {
    data() {
        return {
            categories: [],
            products  : [],
        };
    },
    components: {
      ProductFilter,
      ProductList,
    },
    mounted() {
        fetch('https://dummyjson.com/products/categories').then(res => res.json()).then(json => this.categories = json);
        fetch('https://dummyjson.com/products').then(res => res.json()).then(json => this.products = json.products);
    },
}
</script>

<template>
    <main class="flex justify-center h-full w-full">
        <ProductFilter :categories="categories"/>
        <ProductList :products="products"/>
    </main>
</template>

<style scoped>
@import "tailwindcss";
</style>
