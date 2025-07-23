<script>
import Product from "./Product.vue";

export default {
    data() {
        return {
            displayCategory   : null,
            selectedCategories: [],
        }
    },
    props: {
        products: Array,
    },
    components: {
        Product,
    },
    computed: {
        categories() {
            return [...new Set(this?.products?.map(product => product.category))];
        },
        filteredProducts() {
            return this.products.filter(product => this.selectedCategories.includes(product.category));
        },
    },
    watch: {
        products(oldProducts,newProducts) {
            this.selectedCategories = this.categories;
        },
    },
}
</script>

<template>
    <div class="flex flex-col gap-3 min-w-3/4">
        <div class="flex gap-1 pt-3">
            <label v-for="category in categories" class="bg-blue-500 rounded-md px-2 py-1 text-white">
                <input v-model="selectedCategories" type="checkbox" class="hidden" :value="category" checked/>
                {{ category }}
            </label>
        </div>
        <div class="grid lg:grid-cols-5 md:grid-cols-4 sm:grid-cols-3 gap-5">
            <Product
                v-if="!displayCategory || (displayCategory === this.category)"
                v-for="product in filteredProducts" :key="product.id" :name="product.title" :category="product.category" :image="product.thumbnail"
            />
        </div>
    </div>
</template>

<style lang="css" scoped>
</style>