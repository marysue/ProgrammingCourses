<script setup>
import { defineProps, ref, defineEmits } from 'vue';
const props = defineProps({
    todos: [],
});
const error = ref('');
const emit = defineEmits(['input-complete']);
let newItem = ref('');

function duplicate(inputValue) {
    console.log(`inputValue for duplicates: `, inputValue)
    console.log(`todosArray incoming from parent: `, props.todos);
    const filteredArray = props.todos.length > 0 ? props.todos.filter(x => x.text === inputValue) : [];
    if (filteredArray.length > 0) {
        return true;
    } else {
        return false;
    }
}

function handleInput() {
    if (newItem.value === '') {
        error.value = 'todo item must have a name...';
        return;
    }
    if (duplicate(newItem.value)) {
        console.log(`inputValue:  `, newItem.value);
        error.value = newItem.value + ' already exists in todo';
        event.target.value = '';
        return;
    }
    // emit the custom event to the parent component
    console.log(`emitting input-complete now with inputItem: `, newItem.value);
    emit('input-complete', newItem.value);
    newItem.value = '';
}

</script>

<template>
    <form @submit.prevent="handleInput">
        <input type="text" v-model="newItem" />
        <div class="alert alert-danger =" role="alert"
            style="margin-left: 0px; margin-top: 0px; margin-bottom: 0px; margin-right: 700px" v-if="error !== ''">
            <div style="margin-left: 0px; margin-top: 0px; margin-right: 0px">
                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor"
                    class="bi bi-exclamation-triangle-fill" viewBox="0 0 16 16">
                    <path
                        d="M8.982 1.566a1.13 1.13 0 0 0-1.96 0L.165 13.233c-.457.778.091 1.767.98 1.767h13.713c.889 0 1.438-.99.98-1.767zM8 5c.535 0 .954.462.9.995l-.35 3.507a.552.552 0 0 1-1.1 0L7.1 5.995A.905.905 0 0 1 8 5m.002 6a1 1 0 1 1 0 2 1 1 0 0 1 0-2" />
                </svg>
                {{ error }}
            </div>
        </div>
        <button type="submit">Submit </button>
    </form>
</template>
