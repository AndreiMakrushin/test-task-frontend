<script setup>
import { ref } from 'vue'

const leftBlock = ref([
  { id: 1, name: 'Shoes 1' },
  { id: 2, name: 'Shoes 2' },
  { id: 3, name: 'Shoes 3' },
  { id: 4, name: 'Shoes 4' },
  { id: 5, name: 'T-shirt 1' },
  { id: 6, name: 'T-shirt 2' },
  { id: 7, name: 'T-shirt 3' },
  { id: 8, name: 'T-shirt 4' }
])
const rightBlock = ref([
  { id: 11, name: 'Jacket 1' },
  { id: 12, name: 'Jacket 2' },
  { id: 13, name: 'Jacket 3' },
  { id: 14, name: 'Jacket 4' },
  { id: 15, name: 'Hoodie 1' },
  { id: 16, name: 'Hoodie 2' },
  { id: 17, name: 'Hoodie 3' },
  { id: 18, name: 'Hoodie 4' }
])

const selectedLeft = ref([])
const selectedRight = ref([])

const removeItem = (array, item) => {
  array.splice(array.findIndex(el => el.id === item.id), 1)
}

const pushItem = (source, destination, item, limit) => {
  if (destination.value.length === limit) return;
  destination.value.push(item);
  removeItem(source, item)
}

const pushLeft = (item) => pushItem(leftBlock.value, selectedLeft, item, 6)
const pushRight = (item) => pushItem(rightBlock.value, selectedRight, item, 1)
</script>

<template>
  <div>
    <div class="blocks">
      <ul>
        <li v-for="item in selectedLeft" :key="item.id">{{ item.name }}</li>
        <div>Добавлено {{ selectedLeft.length }} из 6</div>
      </ul>
      <ul>
        <li v-for="item in selectedRight" :key="item.id">{{ item.name }}</li>
      </ul>
    </div>

    <div class="blocks">
      <ul>
        <li v-for="item in leftBlock" :key="item.id" @click="pushLeft(item)">{{ item.name }}</li>
      </ul>
      <ul>
        <li v-for="item in rightBlock" :key="item.id" @click="pushRight(item)">{{ item.name }}</li>
      </ul>
    </div>
  </div>
</template>

<style scoped>
.blocks {
  display: flex;
  flex-direction: row;
}
li {
  margin: 15px;
}
ul {
  padding: 30px;
  border: 2px solid black;
  margin: 0 40px;
}
</style>

