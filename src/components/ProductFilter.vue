<script>
import ProductFilterButton from './ProductFilterButton.vue';

export default {
    components: {
        ProductFilterButton,
    },
    props: {
        categories: Array,
    },
}
</script>

<template>
    <div class="flex flex-col gap-1 pt-3">
        <ProductFilterButton v-for="category in this.categories" :category="category"/>
    </div>
</template>