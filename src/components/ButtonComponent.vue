<template>
    <button class="rounded-pill m-3 p-1 px-3 bg-info" @click="handleClick">{{ direction }}</button>
</template>

<script>
export default {
    name: 'ButtonComponent',
    props: ['direction'],
    methods: {
        handleClick(){
            return this.$emit('currentSentenceChangeButton');
        }
    }
}
</script>

<style scoped>

</style>