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

const noteToIdx = {
    'A': 0,
    'B♭': 1,
    'B': 2,
    'C': 3,
    'D♭': 4,
    'D': 5,
    'E♭': 6,
    'E': 7,
    'F': 8,
    'G♭': 9,
    'G': 10,
    'A♭': 11
};

const notes = [
    'A', 
    'B♭',
    'B',
    'C',
    'D♭',
    'D',
    'E♭',
    'E',
    'F',
    'G♭',
    'G',
    'A♭'
];

const stringNotes = [
    7,
    2,
    10,
    5,
    0,
    7
];

const amPent = [
    'A',
    'C',
    'D',
    'E',
    'G'
];

const indexToNote = (index) => notes[index % Object.keys(notes).length];

</script>

<template>
    <div class="w-screen h-64 relative flex items-stretch">
        <div class="w-20 bg bg-amber-950"></div>
        <div class="w-2 bg-zinc-200"></div>
        <div class="flex content-stretch flex-1 bg-amber-700">
            <div v-for="(dots, index) in frets" class="relative py-10 flex flex-col justify-center content-center flex-1 after:content-[''] after:absolute after:w-1 after:h-full after:right-0 after:bg-gradient-to-r after:bg-zinc-400">
                <div v-for="_ in [...Array(dots).keys()]" class="size-5 m-auto rounded-full bg-zinc-800"></div>
                <div class="absolute z-10 size-full flex flex-col justify-stretch items-stretch">
                    <div v-for="string in stringNotes" class="flex-1">
                        <Note v-if="amPent.includes(indexToNote(string + index + 1))" :note="indexToNote(string + index + 1)" />
                    </div>
                </div>
            </div>
        </div>
        <div class="absolute inset-0 flex flex-col justify-around content-stretch">
            <div v-for="string in stringNotes" class="h-1 shadow-sm bg-gradient-to-b from-zinc-300 via-zinc-200 to-zinc-400"></div>
        </div>
    </div>

    <button @click="frets.push(Object.keys(frets).length % 2 == 0 ? 1 : 0)" class="w-24 h-8 border-2 hover:bg-slate-100">Add Fret</button>
    <button @click="frets.pop()" class="w-24 h-8 border-2 hover:bg-slate-100">Remove Fret</button>
</template>