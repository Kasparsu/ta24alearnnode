<script setup>
import { computed, ref } from 'vue';
let i = 1;
let items = ref([
    {id: i++, text: 'Sai', isDone: true },
    {id: i++, text: 'Piim', isDone: false },
    {id: i++, text: 'Viin', isDone: true },
    {id: i++, text: 'Õlu', isDone: false },
]);
let newItem = ref('');

let doneItems = computed(() => items.value.filter(i => i.isDone));

function add() {
    if(newItem.value.trim() !== ''){
        items.value.push({id: i++, text: newItem.value.trim(), isDone: false });
    }
    newItem.value = '';
}
</script>

<template>
    <div class="container">
        <div class="field has-addons mt-2">
            <div class="control is-expanded">
                <input class="input" type="text" v-model="newItem" @keypress.enter="add">
            </div>
            <div class="control">
                <button class="button is-info" @click="add">
                    Add Item
                </button>
            </div>
        </div>
        <div class="content">
            <h1>All Items</h1>
            <ul>
                <li v-for="item in items">
                    {{ item.text }}
                    <input type="checkbox" v-model="item.isDone">
                </li>
            </ul>

            <h1>Done Items</h1>
            <ul>
                <li v-for="item in doneItems">
                    {{ item.text }}
                    <input type="checkbox" v-model="item.isDone">
                </li>
            </ul>
        </div>
    </div>
</template>

<style></style>