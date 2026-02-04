<script setup>
import { ref } from 'vue';
import Tabs from './components/Tabs.vue';

let titles = ref([
    'Item 1',
    'Item 2',
    'Item 3',
    'Item 4',
]);
let activeTab = ref(0);
let contents = ref([
    'Content 1',
    'Content 2',
    'Content 3',
    'Content 4',
]);
</script>

<template>
    <Tabs :titles="titles" :active="activeTab" @setActive="activeTab=$event"></Tabs>
    <div class="container">
        {{ contents[activeTab] }}
    </div>
</template>

<style></style>