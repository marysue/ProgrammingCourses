<script setup>
import { reactive, ref } from 'vue';
// const myArray = reactive([1, 2, 3]);
const messageRef = ref('Hello World!');
const messageReact = reactive({ message: 'From message react' })
const counter = reactive({ count: 0 });
const myArray = reactive([1, 2, 3]);
console.log(`myArray:  `, myArray);
console.log(`myArray.value: `, myArray.value);
console.log(`myArray[1].value: `, myArray[1].value);
console.log(`myArray[1]:  `, myArray[1]);
myArray[1] = 456;
counter.count = 899;
console.log(`counter.count: `, counter.count);
// console.log(`counter.count.value: `, counter.count.value);
// console.log(`counter.value: `, counter.value);

console.log(`messageRef: `, messageRef);
console.log(`messageRef.value: `, messageRef.value);
console.log(`messageReact: `, messageReact);
console.log(`messageReact.message: `, messageReact.message);
messageRef.value = "Changed message";
messageReact.message = "reactive message changed";
myArray.push(4);
console.log(`pushed "4" into myArray [1,2,3].  Contents is now: `, myArray);
// console.log(`messageReact.message.value: `, messageReact.message.value);


// const myString = ref('Foo Bar');

</script>
<template>
    <div>counter: {{ counter.count }}</div>
    <div>myArray: {{ myArray }}</div>
    <div>myArray[1]: {{ myArray[1] }}</div>
    <div>messageRef: {{ messageRef }}</div>
    <div>messageReact.message: {{ messageReact.message }}</div>
</template>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
    margin: 40px 0 0;
}

ul {
    list-style-type: none;
    padding: 0;
}

li {
    display: inline-block;
    margin: 0 10px;
}

a {
    color: #42b983;
}
</style>
