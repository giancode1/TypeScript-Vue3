<script setup lang="ts">

const emit = defineEmits<{
    (event: 'add-count', count: number): void;
    (event: 'reset-count'): void;

}>()
</script>

<template>
    <div>
        <button @click="emit('add-count', 5)">Add 5</button>
        <button @click="emit('reset-count')">Reset</button>
    </div>
</template>



<style scoped>
</style>