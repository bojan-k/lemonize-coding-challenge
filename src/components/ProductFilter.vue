<script>
import ProductFilterButton from './ProductFilterButton.vue';

export default {
    components: {
        ProductFilterButton,
    },
    emits: ["update:selectedCategories"],
    props: {
        categories        : Array,
        selectedCategories: Set,
    },
    methods: {
        onFilterChange(categorySlug,isSelected) {
            if (isSelected) {
                this.selectedCategories.add(categorySlug);
            } else {
                this.selectedCategories.delete(categorySlug);
            }
            this.$emit("update:selectedCategories",this.selectedCategories);
        },
    },
}
</script>

<template>
    <div class="flex flex-col gap-1">
        <ProductFilterButton v-for="category in this.categories" @change="this.onFilterChange" :category="category"/>
    </div>
</template>