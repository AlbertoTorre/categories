
<template>
    <div class="border border-blue-500 p-2">
        {{ category.name }}: ({{ category.child.length }})
        <button class="btn" @click="add"> Add </button>
        <Category 
            v-for="category in category.child" 
            :category="category"
            @add="(child, parentCategory) => addChildCategory(child, parentCategory)"
        />
    </div>
</template>

<script setup>
const { category } = defineProps(['category'])

const emit = defineEmits(['add'])

const add = () => {
    const order = category.child.length + 1

    emit('add', { name: 'child-'+ order, child: [], parentCategory: category })
}

const addChildCategory = (child, parentCategory) => {

    emit('add', child, parentCategory)
}
</script>
