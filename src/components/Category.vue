
<template>
    <div class="border border-blue-500 p-2">
        {{ category.name }}: ({{ category.child.length }})
        <button class="btn" @click="add"> Add </button>
        <Category 
            v-for="(category, idx) in category.child" 
            :category="category"
            @add="(category) => addChildCategory(category, idx)"
        />
    </div>
</template>

<script setup>
import { watch } from 'vue';

const { category, parentIdx } = defineProps(['category', 'parentIdx'])

const emit = defineEmits(['add'])

const add = () => {

    console.log('add')

    const order = category.child.length + 1

    emit('add', { name: 'child-'+ order, child: [] }, parentIdx )
}

const addChildCategory = (category, idx) => {
    console.log('addChildCategory')
    emit('add', category, idx)
}

watch(
    () => category,
    ()=> {
        console.log('category changed')
    }, 
    { deep: true }
)
</script>