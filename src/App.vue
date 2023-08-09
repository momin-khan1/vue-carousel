<script setup>
import { nextTick, onMounted, ref } from "vue";

const items = ref([
  "https://images.pexels.com/photos/2422915/pexels-photo-2422915.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
  "https://images.pexels.com/photos/3367619/pexels-photo-3367619.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
  "https://images.pexels.com/photos/955657/pexels-photo-955657.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
  "https://images.pexels.com/photos/163391/sunrise-sun-skies-nature-163391.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
  "https://images.pexels.com/photos/1632778/pexels-photo-1632778.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
]);

let carousel = null;
const newItem = ref('https://images.pexels.com/photos/2915263/pexels-photo-2915263.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1')


onMounted(() => {
  carousel = new Flickity('.items', {})
})

const addNewItem = () => {
  items.value.push(newItem.value)
  carousel.destroy()
  nextTick(() => {
    carousel = new Flickity('.items', {})
  })
}


</script>

<template>
  <div class="my-10">
    <input type="text" v-model="newItem"/>
    <button
      @click="addNewItem"
      class="ml-2 bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded"
    >
      Button
    </button>
  </div>

  <div class="mx-auto items">
    <div
      :style="`background-image :url(${item})`"
      v-for="(item, index) in items"
      :key="index"
      class="item"
    >
      {{ index + 1 }}
    </div>
  </div>
</template>

<style scoped>
.items {
  width: 600px;
  height: 400px;
}

.item {
  width: 600px;
  height: 400px;
  background-color: #ccc;
  background-size: cover;
}
</style>
