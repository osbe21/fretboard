<script setup>
import { ref, defineProps } from 'vue';

const props = defineProps(['note']);

</script>

<template>
    <div class="flex justify-center items-center size-full">
        <div class="size-7 rounded-full flex justify-center items-center bg-blue-600">
            <p class="text-white text-lg h-min">{{ props.note }}</p>
        </div>
    </div>
</template>