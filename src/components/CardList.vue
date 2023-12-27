<script setup>
import Card from "@/components/Card.vue";

defineProps({
  items: Array
})

const onClickAdd = () => {
  alert('Добавить')
}

</script>

<template>
  <div class="grid grid-cols-4 gap-2">
    <Card
        :key="item.id"
        v-for="item in items"
        :imageUrl="item.imageUrl"
        :title="item.title"
        :price="item.price"
        :on-click-add="onClickAdd"
        :is-added="true"
        :is-favorite="false"
    />
  </div>
</template>