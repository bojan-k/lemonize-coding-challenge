<script>
import ProductFilterButton from './ProductFilterButton.vue';

export default {
    data() {
        return {
            selectedCategories: new Set(),
        };
    },
    components: {
        ProductFilterButton,
    },
    emits: ["change"],
    props: {
        categories: Array,
    },
    methods: {
        onFilterChange(categorySlug,isSelected) {
            if (isSelected) {
                this.selectedCategories.add(categorySlug);
            } else {
                this.selectedCategories.delete(categorySlug);
            }
        },
    },
    watch: {
        // Initial alle Kategorien auswählen.
        categories(_,newCategories) {
            this.selectedCategories = new Set(this.categories.map(category => category.slug));
        }
    },
}
</script>

<template>
    <div class="flex flex-col gap-1 pt-3">
        <ProductFilterButton v-for="category in this.categories" @change="this.onFilterChange" :category="category"/>
    </div>
</template>