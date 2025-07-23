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
    <div class="grid xl:grid-cols-5 lg:grid-cols-4 md:grid-cols-3 sm:grid-cols-2 xs:grid-cols-1 gap-2 xl:w-[1800px]">
        <Product v-for="product in products" :key="product.id" :product="product"/>
    </div>
</template>

<style lang="css" scoped>
</style>