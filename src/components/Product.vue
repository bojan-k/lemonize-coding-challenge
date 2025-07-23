<script>
export default {
    props: {
        product: Object,
    },
}
</script>

<template>
    <div class="flex flex-col border border-neutral-200 rounded-lg h-[250px] p-3">
        <span class="text-lg text-nowrap text-ellipsis shrink overflow-hidden">{{ this.product.title }}</span>
        <img v-if="this.product.images.length" :src="this.product.images[0]" class="self-center w-2/3">
        <i class="text-sm text-right">{{ this.product.price }} €</i>
    </div>
</template>

<style lang="css" scoped>
</style>