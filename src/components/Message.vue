<script setup lang="ts">
import { ref } from 'vue';

// defineProps<{ msg: string }>();
interface Props {
    msg: string;
    msg1?: string;
}
const props = withDefaults(defineProps<Props>(),{
    msg1: 'default msg1'
});


</script>

<template>
<div>
    <h4>{{ msg }}</h4>
    <h4>{{ msg1 }}</h4>
</div>

</template>

<style scoped>
div{
    background-color: powderblue;
    padding: 1px;
}
</style>
