<script setup>
import Card from "@/components/Card.vue";
</script>

<template>
  <div class="grid grid-cols-4 gap-2">
    <Card imageUrl="/sneakers/sneakers-1.jpg" title="Мужские кроссовки" :price="1205" is-added is-favorite/>
    <Card imageUrl="/sneakers/sneakers-1.jpg" title="Мужские кроссовки" :price="1205"/>
    <Card/>
    <Card/>
    <Card/>
    <Card/>
    <Card/>
  </div>
</template>