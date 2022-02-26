<script setup lang="ts">
import { computed, onMounted, ref } from 'vue';
import fetchCount from '../fecthCount';
import ControlBar from './ControlBar.vue';

// defineProps<{ msg: string }>();
// * Compiler Macro just in setup TypeScript
// * only executed in compile-time
// * no need to be imported

//simple:
// const props = defineProps<{ 
//     limit:number;
//     alertMessageOnLimit:string;
// }>();

//more control:
interface Props {
    limit: number;
    alertMessageOnLimit: string;
}
const props = defineProps<Props>();



const count = ref<number | null>(null);
const product1 = computed(() => {
    if (count.value !== null) {
        return count.value * 2;
    }
    return null;
})



onMounted(() => {
    fetchCount((initialCount) => {
        count.value = initialCount;
    });
});

function addCount(num: number) {
    if (count.value !== null) {
        if (count.value >= props.limit) {
            alert(props.alertMessageOnLimit);
            console.log("se paso");
        } else {
            count.value += num;
        }
    }
}

</script>

<template >
    <div>
        <button type="button" @click="addCount(10)">count is: {{ count }}</button>
        <p>Product * 2 : {{ product1 }}</p>
        <ControlBar 
            @add-count="addCount"
            @reset-count="count=0"
        />
    </div>
</template>

<style scoped>
div{
    background-color: gainsboro;
    padding: 1px;
}
</style>
