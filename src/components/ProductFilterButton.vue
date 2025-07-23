<script>
export default {
    emits: ["change"],
    props: {
        category: Object,
        selected: Boolean,
    },
    methods: {
        onChange(evt) {
            this.$emit("change",this.category.slug,evt.target.checked);
        },
    },
}
</script>

<template>
    <label class="border border-blue-200 rounded-md px-2 py-1 cursor-pointer select-none text-nowrap" :class='{ "bg-blue-500 hover:bg-blue-600 text-white": this.selected, "bg-white hover:bg-gray-100": !this.selected }'>
        <input @change="this.onChange" type="checkbox" class="hidden" :value="this.category.slug" :checked="this.selected"/>
        {{ this.category.name }}
    </label>
</template>