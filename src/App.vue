<script>
import ProductFilter from './components/ProductFilter.vue'
import ProductList   from './components/ProductList.vue'

export default {
    data() {
        return {
            allCategories     : [],
            selectedCategories: new Set(),
            allProducts       : [],
        };
    },
    computed: {
        filteredProducts() {
            return this.allProducts?.filter(product => this.selectedCategories.has(product.category)) ?? [];
        },
    },
    components: {
      ProductFilter,
      ProductList,
    },
    mounted() {
        fetch('https://dummyjson.com/products/categories').then(res => res.json()).then(json => {
            this.allCategories = json;
            json.forEach(category => this.selectedCategories.add(category.slug)); // Initial alles auswählen.
        });
        fetch('https://dummyjson.com/products').then(res => res.json()).then(json =>
            this.allProducts = json.products
        );
    },
}
</script>

<template>
    <main class="flex flex-row justify-center items-start gap-2 pt-2 h-full w-full">
        <ProductFilter :categories="allCategories" v-model:selected-categories="selectedCategories"/>
        <ProductList :products="filteredProducts"/>
    </main>
</template>

<style scoped>
@import "tailwindcss";
</style>
