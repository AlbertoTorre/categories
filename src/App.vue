<template>
    <div class="container mx-auto">
        <h1 class="text-2xl text-blue-600 py-1">
            Categorias ({{ categories.length }})
            <button class="btn">add</button>
        </h1>

        <Category 
          v-for="(category, idx) in categories"
          :category="category"
          :parentIdx="idx"
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

const addChildCategory = (category, idx) => {
    console.log('Ancestro: ', category.name, idx)
    categories.value[idx].child.push(category)
}
</script>