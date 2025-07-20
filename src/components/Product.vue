<script>
export default {
    props: {
        name: String,
    },
}
</script>

<template>
    <span>{{ this.name }}</span>
</template>

<style lang="css" scoped>
@import "tailwindcss";
</style>