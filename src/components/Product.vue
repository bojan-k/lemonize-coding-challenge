<script>
export default {
    props: {
        product: Object,
    },
}
</script>

<template>
    <div class="flex flex-col border border-neutral-200 rounded-lg bg-white h-[250px] w-auto min-w-[200px] p-3 cursor-pointer box-border transition-[transform,box-shadow] hover:scale-101 hover:shadow-md">
        <span class="text-lg text-nowrap text-ellipsis shrink overflow-hidden">{{ this.product.title }}</span>
        <img v-if="this.product.images.length" :src="this.product.images[0]" class="self-center h-2/3">
        <span class="grow"></span>
        <i class="text-sm text-right">{{ this.product.price }} €</i>
    </div>
</template>

<style lang="css" scoped>
</style>