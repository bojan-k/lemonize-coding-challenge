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
    methods: {
        loadCategories() {
            fetch('https://dummyjson.com/products/categories?limit=0').then(res => res.json()).then(json => {
                this.allCategories = json;
                json.forEach(category => this.selectedCategories.add(category.slug)); // Initial alles auswählen.
            });
        },
        loadProducts() {
            fetch('https://dummyjson.com/products?limit=0&select=category,title,images,price').then(res => res.json()).then(json =>
                this.allProducts = json.products
            );
        },
        onSelectAll() {
            this.selectedCategories = new Set(this.allCategories.map(category => category.slug));
        },
        onSelectNone() {
            this.selectedCategories.clear();
        }
    },
    mounted() {
        this.loadCategories();
        this.loadProducts();
    },
}
</script>

<template>
    <main class="flex flex-row justify-center items-start gap-2 pt-2 h-full w-full">
        <ProductFilter
            :categories="allCategories"
            v-model:selected-categories="selectedCategories"
            @select-all="this.onSelectAll"
            @select-none="this.onSelectNone"
        />
        <ProductList
            :products="filteredProducts"
        />
    </main>
</template>

<style scoped>
@import "tailwindcss";
</style>
