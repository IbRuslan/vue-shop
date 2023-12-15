<script setup>
defineProps({
  title: String,
  num: Number
})
</script>

<template>
  <p>Это мой {{title}}: {{num}}</p>
  <button>Йоо</button>
</template>