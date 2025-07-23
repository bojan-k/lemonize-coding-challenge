<script>
export default {
    data() {
        return {
            selected  : true,
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
    <label class="border border-blue-200 rounded-md px-2 py-1 cursor-pointer select-none" :class='{ "bg-blue-500 hover:bg-blue-600 text-white": this.selected, "bg-white hover:bg-gray-100": !this.selected }'>
        <input v-model="selected" @change="this.onChange" type="checkbox" class="hidden" :value="this.category.slug" checked/>
        {{ this.category.name }}
    </label>
</template>