<script>
export default {
    data() {
        return {
            selected: true,
        };
    },
    emits: ["change"],
    props: {
        category: Object,
    },
    methods: {
        onChange() {
            this.$emit("change",this.category.slug,this.selected);
        },
    },
}
</script>

<template>
    <label class="bg-blue-500 rounded-md px-2 py-1 text-white">
        <input v-model="selected" @change="this.onChange" type="checkbox" class="" :value="this.category.slug" checked/>
        {{ this.category.name }}
    </label>
</template>