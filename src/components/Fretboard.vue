<script setup>
import { reactive } from 'vue';
import Note from './Note.vue';

const frets = reactive([
    0,
    0,
    1,
    0,
    1,
    0,
    1,
    0,
    0,
    2,
    0,
    0,
    1,
    0,
    1
]);

</script>

<template>
    <div class="w-screen h-52 relative flex items-stretch">
        <div class="w-20 bg bg-amber-950"></div>
        <div class="w-2 bg-zinc-200"></div>
        <div class="flex content-stretch flex-1 bg-amber-700">
            <div v-for="dots in frets" class="flex flex-col justify-center content-center flex-1 relative after:content-[''] after:absolute after:w-1 after:h-full after:right-0 after:bg-gradient-to-r after:bg-zinc-400">
                <div v-for="_ in [...Array(dots).keys()]" class="w-5 h-5 m-auto rounded-full bg-slate-100"></div>
            </div>
        </div>
        <div class="absolute inset-0 flex flex-col justify-around content-stretch">
            <div v-for="string in [0, 1, 2, 4, 5]" class="h-1 shadow-sm bg-gradient-to-b from-zinc-300 via-zinc-200 to-zinc-400"></div>
        </div>
    </div>

    <button @click="frets.push(Object.keys(frets).length % 2 == 0 ? 1 : 0)" class="w-24 h-8 border-2 hover:bg-slate-100">Add Fret</button>
    <button @click="frets.pop()" class="w-24 h-8 border-2 hover:bg-slate-100">Remove Fret</button>
</template>