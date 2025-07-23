<script>
import ProductFilterButton from './ProductFilterButton.vue';

export default {
    components: {
        ProductFilterButton,
    },
    emits: ["update:selectedCategories","select-all","select-none"],
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
        onSelectAll() {
            this.$emit("select-all");
        },
        onSelectNone() {
            this.$emit("select-none");
        }
    },
}
</script>

<template>
    <div class="flex flex-col gap-1">
        <button
            type="button"
            class="border border-blue-200 rounded-md bg-blue-500 hover:bg-blue-600 active:scale-98 text-white px-2 py-1 cursor-pointer select-none"
            @click="this.onSelectAll"
        >
            alles auswählen
        </button>
        <button
            type="button"
            class="border border-blue-200 rounded-md bg-blue-500 hover:bg-blue-600 active:scale-98 text-white px-2 py-1 cursor-pointer select-none"
            @click="this.onSelectNone"
        >
            nichts auswählen
        </button>
        <span class="h-1"></span>
        <ProductFilterButton v-for="category in this.categories" @change="this.onFilterChange" :category="category" :selected="this.selectedCategories.has(category.slug)"/>
    </div>
</template>