<script>
import Product from "./Product.vue";

export default {
    props: {
        products: Array,
    },
    components: {
        Product,
    },
}
</script>

<template>
    <div class="flex flex-row gap-3">
        <div class="grid lg:grid-cols-5 md:grid-cols-4 sm:grid-cols-3 gap-5">
            <Product
                v-for="product in products" :key="product.id" :name="product.title" :category="product.category" :image="product.thumbnail"
            />
        </div>
    </div>
</template>

<style lang="css" scoped>
</style>