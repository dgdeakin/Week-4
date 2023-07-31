<script setup>
import { ref } from 'vue'

const message = ref('Hello World!')
const show = ref(true)
const list = ref([1, 2, 3])

function reverseMessage() {
  // Access/mutate the value of a ref via
  // its .value property.
  message.value = message.value.split('').reverse().join('')
}

function notify() {
  alert('navigation was prevented.')
}
</script>

<template>
  <h1> {{ message }}</h1>
  <br>
  <button @click="reverseMessage">Reverse Message</button>

  <button @click="message += 'Added to the message!'">Append</button>

  <div>
    <button @click="show = !show">Toggle List</button>
    <button @click="list.push(list.length + 1)">Push Number</button>
    <button @click="list.pop()">Pop Number</button>
    <button @click="list.reverse()">Reverse List</button>

    <ul v-if="show && list.length">
      <li v-for="item of list">{{ item }}</li>
    </ul>
    <p v-else-if="list.length">List is not empty, but hidden.</p>
    <p v-else>List is empty.</p>
  </div>
</template>
<style scoped>
</style>
