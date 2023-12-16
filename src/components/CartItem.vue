<script setup>
defineProps({
  title: String,
  imageUrl: String,
  price: Number,
  onClickDelete: Function,
})
</script>

<template>
  <div class="flex items-center border border-slate-200 p-4 rounded-xl gap-4">
    <img class="w-16 h-16" :src="imageUrl" alt="sneaker">

    <div class="flex flex-col">

      <p>{{title}}</p>

      <div class="flex justify-between mt-2">
        <b>{{price}} руб.</b>
        <img @click="onClickDelete" class="opacity-40 hover:opacity-100 cursor-pointer transition" src="/close.svg" alt="delete">
      </div>

    </div>
  </div>
</template>