<script>
import ProductFilterButton from './ProductFilterButton.vue';

export default {
    data() {
        return {
            selectedCategories: [],
        }
    },
    components: {
        ProductFilterButton,
    },
    props: {
        categories: Array,
    },
    watch: {
        // Initial alle Kategorien auswählen.
        categories(_,newCategories) {
            this.selectedCategories = newCategories.map(category => category.slug);
        },
    },
}
</script>

<template>
    <div class="flex flex-col gap-1 pt-3">
        <ProductFilterButton v-for="category in this.categories" :category="category"/>
    </div>
</template>