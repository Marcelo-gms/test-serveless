<template>
  <div class="">
    <h1 style="text-align: center">Show, Deu certo!</h1>
    <h1 style="text-align: center">{{ msg }}</h1>
  </div>
</template>
<script setup>
import { computed } from "vue";
import { ref } from "vue";

const message = ref("");
const msg = computed(() => message.value);
async function getData() {
  const request = await fetch(".netlify/functions/hello");
  const dataResponse = await request.json();

  message.value = dataResponse.message;
}

getData();
</script>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
