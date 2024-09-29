<template>
  <v-container fluid class="d-flex justify-center flex-column">
    <img src="./assets/logo.svg" width="125" height="125" />

    <v-btn
      class="my-4"
      color="primary"
      prepend-icon="mdi-plus"
      @click="add"
      width="80"
      teste="teste"
    >
      add
    </v-btn>

    <p class="text-h6">{{ count }}</p>
  </v-container>
</template>

<script setup>
import { ref } from 'vue'
const count = ref(0)
const users = ref([])

async function add() {
  count.value++
  console.log(count.value)

  await fetch('https://jsonplaceholder.typicode.com/users')
    .then((response) => response.json())
    .then((res) => {
      console.log(res)
      users.value = res
    })
}
</script>
