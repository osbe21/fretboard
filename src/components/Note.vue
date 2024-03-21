<script setup>
import { ref } from 'vue';

const props = defineProps({
    'scale': Array,
    'note': String,
});

const show = ref(false);

</script>

<template>
    <div @click="show = props.scale.includes(props.note)"  class="flex justify-center items-center size-full select-none">
        <div v-if="show" class="size-7 rounded-full flex justify-center items-center bg-blue-600">
            <p class="text-white text-lg h-min">{{ props.note }}</p>
        </div>
    </div>
</template>