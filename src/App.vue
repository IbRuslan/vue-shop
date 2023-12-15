<script setup>
import MyHello from "@/components/MyHello.vue";
import {ref} from 'vue'

let count = ref(1);

const increment = () => {
  count.value += 1
}
</script>

<template>
  <div>
    <h1 class="mb-28 text-center">{{count}}</h1>
    <button @click="increment">+</button>
  </div>
  <div>
    <MyHello title="номер" :num="999"/>
  </div>
</template>

<style scoped>

</style>
