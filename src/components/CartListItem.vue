<script setup>
import CartItem from "@/components/CartItem.vue";
</script>

<template>
  <div class="flex flex-col gap-5">
    <CartItem imageUrl="/sneakers/sneakers-1.jpg" title="Мужские кроссовки Nike" :price="1205"/>
    <CartItem imageUrl="/sneakers/sneakers-2.jpg" title="Мужские кроссовки Nike" :price="1205"/>
    <CartItem imageUrl="/sneakers/sneakers-3.jpg" title="Мужские кроссовки Nike" :price="1205"/>
  </div>
</template>
