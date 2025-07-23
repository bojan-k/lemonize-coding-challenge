<script>
export default {
    props: {
        name    : String,
        category: String,
        image   : String,
    },
}
</script>

<template>
    <div class="flex flex-col border border-neutral-200 rounded-lg h-[250px] p-3">
        <h1>{{ this.name }}</h1>
        <img :src="this.image" class="self-center w-2/3">
    </div>
</template>

<style lang="css" scoped>
</style>