<script setup>
    import { defineProps } from 'vue';

    const props = defineProps(['resultado'])
</script>

<template>
    <div class="text-center border border-dark rounded p-5">
        <h1>Resultado:</h1>
        <h1 class="display-1">{{props.resultado}}</h1>
    </div>
</template>

<style scoped>

</style>