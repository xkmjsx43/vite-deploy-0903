<template>
  <div class="about">
    <h1>This is an about page</h1>
    <pre>{{ data }}</pre>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
<script setup>
console.log(import.meta.env.VITE_TEXT)
console.log(import.meta.env.VITE_PATH)
import { ref, onMounted } from 'vue'
import axios from 'axios'

const data = ref({})

onMounted(() => {
  const url = import.meta.env.VITE_PATH
  axios.get(url)
    .then((res) => {
      console.log(res)
      data.value = res.data.results[0]
    })
});
</script>