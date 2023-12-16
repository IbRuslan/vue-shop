<script setup>
defineProps({
  title: String,
  imageUrl: String,
  price: Number,
  isFavorite: Boolean,
  isAdded: Boolean,
  onClickAdd: Function,
  onClickFavorite: Function
})
</script>

<template>
  <div class="relative bg-white m-10 border border-slate-100 rounded-3xl p-8 cursor-pointer transition hover:-translate-y-2 hover:shadow-xl">
    <img class="absolute top-8 left-8" :src="isFavorite ? '/like-2.svg' : '/like-1.svg' " @click="onClickFavorite" alt="like">
    <img :src="imageUrl" alt="sneaker">
    <p class="mt-2">{{title}}</p>
    <div class="flex justify-between mt-5">
      <div class="flex flex-col">
        <span class="text-slate-400">Цена</span>
        <b>{{price}} руб.</b>
      </div>
      <img :src="!isAdded ? '/plus.svg' : '/checked.svg' " @click="onClickAdd" alt="plus">
    </div>
  </div>
</template>