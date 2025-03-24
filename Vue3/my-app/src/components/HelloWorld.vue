<script setup>
import { ref } from 'vue';
import addToDo from './addTodo.vue'

let id = 0;
const status = ref('waiting...');
const messageRef = ref('Hello World!');
const todosRef = ref([
])
console.log(`todosRef: `, todosRef.value)
const count = ref(0);
const myArray = ref([1, 2, 3]);

// const myHTML = '<span style="color: red">Red</span>'
myArray.value[1] = 456;
count.value = 899;
messageRef.value = "Changed message";
messageRef.value = "reactive message changed";
myArray.value.push(4);

function addToDoItem(item) {
    console.log(`addToDoItem is the emitted function with item:  `, item);
    status.value = 'addToDoItem called'
    console.log(`adding item:  `, item);
    todosRef.value.push({ id: id++, text: item })
    console.log(`new todosRef:  `, todosRef.value);
    status.value = 'Added ' + item + ' ...'
}

</script>

<template>
    <div>
        <h2>Todos:</h2>
        <ul>
            <li v-for="(todo, id) in todosRef" :key="id" style="display: list-item">
                {{ todo.text }}
            </li>
        </ul>

        <addToDo :todos="todosRef" @input-complete="addToDoItem" />
    </div>
</template>

<style>
div {
    margin-left: 250px;
    text-align: left;
}


li {
    list-style-type: none;
}

a {
    color: #42b983;
}
</style>
