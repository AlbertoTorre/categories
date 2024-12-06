<template>
  <div class="container mx-auto">
      <h1 class="text-2xl text-blue-600 py-1">
          Categorias ({{ categories.length }})
          <button class="btn" @click="addCategory">Add</button>
      </h1>

      <Category 
        v-for="category in categories"
        :key="category.id"
        :category="category"
        @add="addChildCategory"
      />
  </div>
</template>

<script setup>
import { ref } from 'vue'

import Category from './components/Category.vue'

const categories = ref([
  { id: 1, name: 'cat1', child: []},
  { id: 2, name: 'cat2', child: []},
  { id: 3, name: 'cat3', child: []},
])

const addCategory = () => {
  const newCategory = { name: `cat${categories.value.length + 1}`, child: [] }
  categories.value.push(newCategory)
}
const addChildCategory = (category, childCategory) => {
  category.child.push(childCategory)
}
</script>
