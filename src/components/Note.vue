<script setup>
import { ref } from 'vue';

const note = ref('B♭');

</script>

<template>
    <div class="size-10 rounded-full flex justify-center items-center bg-red-600">
        <p class="text-white text-lg h-min">{{ note }}</p>
    </div>
</template>