<script setup>
import {onMounted, reactive, ref, watch} from "vue";
import axios from "axios";

import Header from "@/components/Header.vue";
import CardList from "@/components/CardList.vue";
import Drawer from "@/components/Drawer.vue";

const items = ref([])
const filters = reactive({
  sortBy: '',
  searchQuery: ''
})

const onChangeSelect = (e) => {
  filters.sortBy = e.target.value
}

const onChangeSearchInput = (e) => {
  if (e.target.value.trim() !== '') {
    filters.searchQuery = e.target.value.trim()
  }
}

const fetchItems = async () => {
  try {
    const params = {
      sortBy: filters.sortBy,
    }
    if(filters.searchQuery) {
      params.title = `*${filters.searchQuery}*`
    }

    const {data} = await axios.get('https://604781a0efa572c1.mokky.dev/items', {
      params
    })

    items.value = data.map(item => ({...item, isFavorite: false, isAdded: false}))
  } catch (e) {
    console.log(e)
  }
}

const fetchFavorites = async () => {
  try {
    const {data: favorites} = axios.get('https://604781a0efa572c1.mokky.dev/favorites')

    items.value = items.value.map(item => {
      const favorite = favorites.find(favorite => favorite.parentId === item.id)
      if(!favorite) {
        return item
      }
      return  {
        ...item,
        isFavorite: true
      }
    })
  } catch (e) {
    console.log(e)
  }
}

onMounted( async () => {
  await fetchItems()
  await fetchFavorites()
})
watch(filters, fetchItems)
</script>

<template>
<!--  <Drawer/>-->
  <div class="bg-white w-4/5 m-auto rounded-xl shadow-xl mt-14">

    <Header/>

    <div class="p-10">
      <div class="flex justify-between items-center">
        <h2 class="text-3xl font-bold mb-8">Все кроссовки</h2>

        <div class="flex flex-col gap-4">
          <select @change="onChangeSelect" class="py-2 px-3 border rounded-md outline-none cursor-pointer">
            <option value="name">по названию</option>
            <option value="price">По цене (дешевые)</option>
            <option value="-price">По цене (дорогие)</option>
          </select>

          <div class="relative">
            <img class="absolute left-4 top-3" src="/search.svg" />
            <input @input="onChangeSearchInput" class="border rounded-md py-2 pl-11 pr-4 outline-none focus:border-gray-400" placeholder="Поиск" />
          </div>
        </div>
      </div>

      <CardList :items="items" />
    </div>

  </div>
</template>
